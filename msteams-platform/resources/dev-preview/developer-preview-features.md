---
title: Features in der öffentlichen Developer Preview
description: Details zu den Features in der öffentlichen Microsoft Teams-Developer Preview
ms.topic: reference
keywords: Teams vorschau entwicklerfeatures
ms.openlocfilehash: 05954383931444cd0fb53dc37d9f790257f7dd39
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634516"
---
# <a name="features-in-the-public-developer-preview-for-microsoft-teams"></a><span data-ttu-id="a7104-104">Features in der öffentlichen Developer Preview für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a7104-104">Features in the Public Developer Preview for Microsoft Teams</span></span>

<span data-ttu-id="a7104-105">Die Entwicklervorschau enthält die folgenden neuen Features:</span><span class="sxs-lookup"><span data-stu-id="a7104-105">The developer preview includes the following new features:</span></span>

## <a name="app-customization"></a><span data-ttu-id="a7104-106">App-Anpassung</span><span class="sxs-lookup"><span data-stu-id="a7104-106">App customization</span></span>

<span data-ttu-id="a7104-107">Sie können nun einen ausgewählten Satz von Eigenschaften definieren, den ein Teams-Administrator je nach Bedarf der Organisation anpassen oder neubranden kann.</span><span class="sxs-lookup"><span data-stu-id="a7104-107">You can now define a select set of properties, which a Teams admin can customize or rebrand based on their organization's need.</span></span> <span data-ttu-id="a7104-108">Weitere Informationen finden Sie unter [App-Anpassungsfeature](~/concepts/design/design-teams-app-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a7104-108">For more information, see [app customization feature](~/concepts/design/design-teams-app-overview.md).</span></span>

## <a name="tabs-single-sign-on-sso"></a><span data-ttu-id="a7104-109">Einmaliges Anmelden (Single Sign-On, SSO)</span><span class="sxs-lookup"><span data-stu-id="a7104-109">Tabs single sign-on (SSO)</span></span>

<span data-ttu-id="a7104-110">Sie können jetzt [einmaliges Anmelden (Single Sign-On, SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) verwenden, um sich über das Teams JavaScript SDK über eine Webinhaltsseite anzumelden und einen Benutzer auf Desktop- und Mobilgeräten zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="a7104-110">You can now use [single sign-on (SSO)](~/tabs/how-to/authentication/auth-aad-sso.md) to login and authenticate a user on desktop and mobile using the Teams JavaScript SDK from a web content page.</span></span> <span data-ttu-id="a7104-111">Einer der Vorteile ist, dass sich ein Benutzer niemals anmelden muss. und sobald sie der App mit ihrem Profil zugestimmt haben: Sie werden automatisch auf ihrer Registerkarte (einschließlich Mobile) angemeldet.</span><span class="sxs-lookup"><span data-stu-id="a7104-111">One of the benefits is that a user never has to sign-in; and once they've consented to the app using their profile: they will automatically be signed-in to their tab (including mobile).</span></span>

<span data-ttu-id="a7104-112">Unsere Entwicklervorschau ist in den Manifestversionen 1.5 und höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a7104-112">Our developer preview is available in manifest versions 1.5 and greater.</span></span> <span data-ttu-id="a7104-113">Unsere aktuelle Implementierung kann nur eine begrenzte Anzahl von Graph-APIs abrufen, wir bieten jedoch eine Problemumgehung, um zusätzliche Graph-APIs mithilfe unserer vorhandenen Authentifizierungs-API zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a7104-113">Our current implementation can only get a limited amount of Graph APIs, however we provide a workaround to get additional Graph APIs using our existing authentication API.</span></span>

## <a name="calls-and-online-meeting-bots"></a><span data-ttu-id="a7104-114">Anrufe und Online-Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="a7104-114">Calls and online meeting bots</span></span>

<span data-ttu-id="a7104-115">Durch das Hinzufügen von [Microsoft Graph-APIs](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true)für Anrufe und Onlinebesprechungen können Microsoft Teams-Apps jetzt auf vielfältige Weise mithilfe von Sprach- und Videonachrichten mit Benutzern interagieren.</span><span class="sxs-lookup"><span data-stu-id="a7104-115">With the addition of [Microsoft Graph APIs for calls and online meetings](/graph/api/resources/communications-api-overview?view=graph-rest-beta&preserve-view=true), Microsoft Teams apps can now interact with users in rich ways using voice and video.</span></span> <span data-ttu-id="a7104-116">Mit diesen APIs können Sie neue App-Features wie interaktive Sprachantwort (Interactive Voice Response, IVR), Anrufsteuerung und Zugriff auf Audio- und/oder Videostreams in Echtzeit für Anrufe und Besprechungen hinzufügen, einschließlich Desktop- und App-Freigabe.</span><span class="sxs-lookup"><span data-stu-id="a7104-116">These APIs allow you to add new app features such as interactive voice response (IVR), call control, and access to real-time audio and/or video streams for calls and meetings, including desktop and app sharing.</span></span>

<span data-ttu-id="a7104-117">Wir haben einen neuen Abschnitt zum Erstellen und Entwickeln von Anrufen und Onlinebesprechungsbots hinzugefügt, beginnend mit der [Übersicht](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a7104-117">We've added a new section on how to create and develop calls and online meetings bots, starting with the [overview](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span>


## <a name="image-enlarge-support"></a><span data-ttu-id="a7104-118">Unterstützung für die Bild vergrößern</span><span class="sxs-lookup"><span data-stu-id="a7104-118">Image enlarge support</span></span>

<span data-ttu-id="a7104-119">Bots können jetzt angeben, welche Bilder, die in adaptiven Karten in Teams freigegeben sind, vergrößert werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="a7104-119">It is now possible for bots to indicate which images shared in Adaptive Cards in Teams are allowed to be enlarged.</span></span> <span data-ttu-id="a7104-120">Dies ist nützlich für Szenarien wie das Freigeben detaillierter schrittweiser visueller Anleitungen über Bots, die für Benutzer andernfalls schwer zu lesen sind.</span><span class="sxs-lookup"><span data-stu-id="a7104-120">This is useful for scenarios like sharing detailed step-by-step visual guides via bots which might be hard to read for users otherwise.</span></span> <span data-ttu-id="a7104-121">Um ein Bild erweiterbar zu machen, kennzeichnen Sie es `allowExpand: true` wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a7104-121">To make an image expandable, just flag it `allowExpand: true` as shown below.</span></span>

```json
    {
      "type": "Image",
      "url": "https://picsum.photos/200/200?image=110",
      "msTeams": {
        "allowExpand": true
      }
    }
```
<span data-ttu-id="a7104-122">Dies hat zur Ursache, dass der Web-/Desktopclient von Teams ein Element beim Zeigen auf das Bild rendert, damit der Benutzer das Bild erweitern kann.</span><span class="sxs-lookup"><span data-stu-id="a7104-122">This will cause Teams web/desktop client to render an element on hover over the image to allow the user to expand the image.</span></span>

