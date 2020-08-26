---
title: Features in der Public Developer Preview
description: Details zu den Features in der Public Developer Preview von Microsoft Teams
keywords: Entwicklerfeatures in Microsoft Teams Preview
ms.openlocfilehash: 773e0334bddf45b7b86d31329b99607f3b70c534
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874842"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="0d314-104">Features in der Public Preview für Entwickler von Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0d314-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="0d314-105">Die Entwicklervorschau umfasst die folgenden neuen Features:</span><span class="sxs-lookup"><span data-stu-id="0d314-105">The developer preview includes the following new features:</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="0d314-106">Registerkarten für einmaliges Anmelden (SSO)</span><span class="sxs-lookup"><span data-stu-id="0d314-106">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="0d314-107">Sie können jetzt [einmaliges Anmelden (Single Sign-on, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) für die Anmeldung und Authentifizierung eines Benutzers auf Desktop-und Mobilgeräten verwenden, indem Sie das Microsoft Teams-JavaScript-SDK über eine Webinhalts Seite verwenden.</span><span class="sxs-lookup"><span data-stu-id="0d314-107">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="0d314-108">Einer der Vorteile besteht darin, dass sich ein Benutzer niemals anmelden muss; und nachdem Sie der App mithilfe Ihres Profils zugestimmt haben: Sie werden automatisch auf Ihrer Registerkarte (einschließlich Mobiltelefon) angemeldet.</span><span class="sxs-lookup"><span data-stu-id="0d314-108">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="0d314-109">Unsere Entwicklervorschau steht in Manifest-Versionen 1,5 und höher zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="0d314-109">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="0d314-110">Unsere aktuelle Implementierung kann nur eine beschränkte Menge an Graph-APIs erhalten, aber wir bieten eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="0d314-110">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="0d314-111">Bots für Anrufe und Onlinebesprechungen</span><span class="sxs-lookup"><span data-stu-id="0d314-111">Calls and online meeting bots</span></span>

<span data-ttu-id="0d314-112">Mit [Microsoft Graph-APIs für Anrufe und Onlinebesprechungen](/graph/api/resources/communications-api-overview?view=graph-rest-beta)können Microsoft Teams-apps nun mithilfe von Sprach-und Videofunktionen auf vielfältige Weise mit Benutzern interagieren.</span><span class="sxs-lookup"><span data-stu-id="0d314-112">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="0d314-113">Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Echtzeit-Audio-und/oder-Videodatenströme für Anrufe und Besprechungen einschließlich Desktop-und App-Freigaben hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0d314-113">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="0d314-114">Wir haben einen neuen Abschnitt zum Erstellen und entwickeln von Anrufen und Online-Besprechungs-Bots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0d314-114">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>

## <a name="image-enlarge-support"></a><span data-ttu-id="0d314-115">Unterstützung für Bildvergrößerung</span><span class="sxs-lookup"><span data-stu-id="0d314-115">Image enlarge support</span></span>

<span data-ttu-id="0d314-116">Es ist nun möglich, dass Bots anzeigen, welche in Adaptive Cards in Microsoft Teams freigegebenen Bilder vergrößert werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="0d314-116">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="0d314-117">Dies ist nützlich für Szenarien wie das Freigeben detaillierter Schritt-für-Schritt-visueller Anleitungen über Bots, die andernfalls für Benutzer schwer lesbar sein können.</span><span class="sxs-lookup"><span data-stu-id="0d314-117">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="0d314-118">Um ein Bild erweiterbar zu machen, markieren Sie es einfach `allowExpand: true` wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0d314-118">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="0d314-119">Dadurch wird ein Element des Teams-Webservers/Desktop Clients auf dem Mauszeiger über dem Bild gerendert, damit der Benutzer das Bild erweitern kann.</span><span class="sxs-lookup"><span data-stu-id="0d314-119">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>

