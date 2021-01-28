---
title: Features im öffentlichen Developer Preview
description: Details zu den Features in der öffentlichen Microsoft Teams-Developer Preview
ms.topic: reference
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: 3275ef7ac0d4ba052f417f6e852f48e2fdf267f5
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014355"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="27712-104">Features im öffentlichen Developer Preview für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="27712-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="27712-105">Die Entwicklervorschau enthält die folgenden neuen Features:</span><span class="sxs-lookup"><span data-stu-id="27712-105">The developer preview includes the following new features:</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="27712-106">Einmaliges Anmelden (Single Sign-On, SSO)</span><span class="sxs-lookup"><span data-stu-id="27712-106">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="27712-107">Sie können jetzt einmaliges Anmelden [(Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um sich über das JavaScript SDK von Teams über eine Webinhaltsseite anzumelden und einen Benutzer auf desktop- und mobilen Geräten zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="27712-107">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="27712-108">Einer der Vorteile ist, dass sich ein Benutzer nie anmelden muss. und nachdem sie der App mithilfe ihres Profils zugestimmt haben: Sie werden automatisch bei ihrer Registerkarte (einschließlich Mobilgerät) angemeldet.</span><span class="sxs-lookup"><span data-stu-id="27712-108">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="27712-109">Unsere Entwicklervorschau ist in Manifestversionen 1.5 und höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="27712-109">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="27712-110">Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen. Wir bieten jedoch eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="27712-110">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="27712-111">Anrufe und Online-Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="27712-111">Calls and online meeting bots</span></span>

<span data-ttu-id="27712-112">Durch das Hinzufügen von [Microsoft Graph-APIs für](/graph/api/resources/communications-api-overview?view=graph-rest-beta)Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt mithilfe von Sprache und Video auf vielfältige Weise mit Benutzern interagieren.</span><span class="sxs-lookup"><span data-stu-id="27712-112">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="27712-113">Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videostreams in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.</span><span class="sxs-lookup"><span data-stu-id="27712-113">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="27712-114">Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Anrufen und Onlinebesprechungsbots hinzugefügt, beginnend mit der [Übersicht.](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)</span><span class="sxs-lookup"><span data-stu-id="27712-114">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>

## <a name="image-enlarge-support"></a><span data-ttu-id="27712-115">Unterstützung für Bildgröße</span><span class="sxs-lookup"><span data-stu-id="27712-115">Image enlarge support</span></span>

<span data-ttu-id="27712-116">Bots können jetzt angeben, welche In adaptiven Karten in Teams freigegebenen Bilder vergrößert werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="27712-116">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="27712-117">Dies ist hilfreich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Anleitungen über Bots, die für Benutzer andernfalls schwer zu lesen sein könnten.</span><span class="sxs-lookup"><span data-stu-id="27712-117">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="27712-118">Um ein Bild erweiterbar zu machen, kennzeichnen Sie es `allowExpand: true` wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="27712-118">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="27712-119">Dadurch rendert der Web-/Desktopclient von Teams ein Element beim Zeigen auf das Bild, damit der Benutzer das Bild erweitern kann.</span><span class="sxs-lookup"><span data-stu-id="27712-119">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>

