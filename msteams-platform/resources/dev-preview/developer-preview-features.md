---
title: Features in der öffentlichen Developer Preview
description: Details zu den Features im Microsoft Teams Public Developer Preview
ms.topic: reference
localization_priority: Normal
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: 84683420a5c61bb1eb493f8191bfbcbe97f6fb46
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230904"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="1b58e-104">Features in der öffentlichen Developer Preview für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1b58e-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="1b58e-105">Diese Seite ist im Juni 2021 veraltet.</span><span class="sxs-lookup"><span data-stu-id="1b58e-105">This page will be deprecated in June 2021.</span></span> <span data-ttu-id="1b58e-106">Informationen zu features available for developer preview finden Sie unter [What's new?](~/whats-new.md)</span><span class="sxs-lookup"><span data-stu-id="1b58e-106">For information on features available for developer preview, see [What's new?](~/whats-new.md)</span></span>

<span data-ttu-id="1b58e-107">Die Entwicklervorschau enthält die folgenden neuen Features:</span><span class="sxs-lookup"><span data-stu-id="1b58e-107">The developer preview includes the following new features:</span></span>

## <a name="app-customization"></a><span data-ttu-id="1b58e-108">App-Anpassung</span><span class="sxs-lookup"><span data-stu-id="1b58e-108">App customization</span></span>

<span data-ttu-id="1b58e-109">Sie können jetzt einen ausgewählten Satz von Eigenschaften definieren, den ein Teams Administrator je nach Bedarf der Organisation anpassen oder neubranden kann.</span><span class="sxs-lookup"><span data-stu-id="1b58e-109">You can now define a select set of properties, which a Teams admin can customize or rebrand based on their organization's need.</span></span> <span data-ttu-id="1b58e-110">Weitere Informationen finden Sie unter [App-Anpassungsfeature](~/concepts/design/design-teams-app-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b58e-110">For more information, see [app customization feature](~/concepts/design/design-teams-app-overview.md).</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="1b58e-111">Einmaliges Anmelden (Single Sign-On, SSO)</span><span class="sxs-lookup"><span data-stu-id="1b58e-111">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="1b58e-112">Sie können jetzt einmaliges Anmelden [(Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um sich über das Teams JavaScript SDK über eine Webinhaltsseite anzumelden und einen Benutzer auf Desktop- und Mobilgeräten zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="1b58e-112">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="1b58e-113">Einer der Vorteile ist, dass sich ein Benutzer niemals anmelden muss. und sobald sie der App mit ihrem Profil zugestimmt haben: Sie werden automatisch auf ihrer Registerkarte (einschließlich Mobile) angemeldet.</span><span class="sxs-lookup"><span data-stu-id="1b58e-113">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="1b58e-114">Unsere Entwicklervorschau ist in den Manifestversionen 1.5 und höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1b58e-114">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="1b58e-115">Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen. Wir bieten jedoch eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="1b58e-115">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="1b58e-116">Anrufe und Online-Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="1b58e-116">Calls and online meeting bots</span></span>

<span data-ttu-id="1b58e-117">Durch das Hinzufügen von [Microsoft Graph-APIs](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)für Anrufe und Onlinebesprechungen können Microsoft Teams Apps jetzt mit Benutzern auf vielfältige Weise mithilfe von Sprach- und Videonachrichten interagieren.</span><span class="sxs-lookup"><span data-stu-id="1b58e-117">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="1b58e-118">Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videostreams in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.</span><span class="sxs-lookup"><span data-stu-id="1b58e-118">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="1b58e-119">Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Anrufen und Onlinebesprechungsbots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b58e-119">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>


## <a name="image-enlarge-support"></a><span data-ttu-id="1b58e-120">Unterstützung für die Bild vergrößern</span><span class="sxs-lookup"><span data-stu-id="1b58e-120">Image enlarge support</span></span>

<span data-ttu-id="1b58e-121">Bots können jetzt angeben, welche Bilder in adaptiven Karten in Teams vergrößert werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="1b58e-121">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="1b58e-122">Dies ist nützlich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Anleitungen über Bots, die für Benutzer andernfalls schwer zu lesen sind.</span><span class="sxs-lookup"><span data-stu-id="1b58e-122">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="1b58e-123">Um ein Bild erweiterbar zu machen, kennzeichnen Sie es `allowExpand: true` wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="1b58e-123">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="1b58e-124">Dies hat zur Teams, dass der Web-/Desktopclient beim Zeigen auf das Bild ein Element rendert, damit der Benutzer das Bild erweitern kann.</span><span class="sxs-lookup"><span data-stu-id="1b58e-124">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>
