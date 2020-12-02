---
title: Neuanordnen von Tabs für persönliche apps
description: Vorgehensweise Neuanordnen von statischen Registerkarten der persönlichen app in Ihrer persönlichen App
keywords: Teams-Registerkarten Entwicklung
ms.openlocfilehash: a8a7c3d23bac98ef1085a8f3443ca0fc92ae0a31
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "49554829"
---
# <a name="reorder-personal-app-tabs"></a><span data-ttu-id="72640-104">Neuanordnen von Tabs für persönliche apps</span><span class="sxs-lookup"><span data-stu-id="72640-104">Reorder personal app tabs</span></span>

<span data-ttu-id="72640-105">Beginnend mit manifestVersion 1,7 können Entwickler alle Registerkarten in Ihrer persönlichen APP neu anordnen.</span><span class="sxs-lookup"><span data-stu-id="72640-105">Starting with manifest version 1.7 developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="72640-106">Insbesondere kann ein Entwickler die Registerkarte "bot Chat" (die immer auf die erste Position eingestellt ist) an einer beliebigen Stelle in der Kopfzeile der persönlichen App-Registerkarte verschieben.</span><span class="sxs-lookup"><span data-stu-id="72640-106">In particular, a developer can move the “bot chat” tab (which has always defaulted to the first position) anywhere in the personal app tab header.</span></span> <span data-ttu-id="72640-107">Wir haben zwei reservierte Registerkarten Entität-Schlüsselwörter deklariert: "Unterhaltungen" und "about".</span><span class="sxs-lookup"><span data-stu-id="72640-107">We’ve declared two reserved tab entityId keywords: “conversations” and “about”.</span></span>

## <a name="moving-the-chatconversation-tab"></a><span data-ttu-id="72640-108">Verschieben der Registerkarte "Chat/Unterhaltung"</span><span class="sxs-lookup"><span data-stu-id="72640-108">Moving the “Chat/Conversation” tab</span></span>

<span data-ttu-id="72640-109">Wenn Sie einen bot mit einem "persönlichen" Bereich erstellen, wird er immer an der ersten Registerkarten Position in einer persönlichen App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="72640-109">If you create a bot with a “personal” scope, it will always show up in the first tab position in a personal app.</span></span> <span data-ttu-id="72640-110">Wenn Sie es an eine andere Position verschieben möchten, müssen Sie dem Manifest ein statisches Tab-Objekt mit dem reservierten Schlüsselwort "Conversations" hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="72640-110">If you wish to move it to another position, you need to add a static tab object to your manifest with the reserved keyword “conversations”.</span></span> <span data-ttu-id="72640-111">Überall dort, wo Sie die Registerkarte "Unterhaltungen" im Array "staticTabs" hinzufügen, wird die Registerkarte Unterhaltung auf dem Bildschirm "Internet" und "Desktop" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="72640-111">Wherever you add the “conversations” tab in the “staticTabs” array, that’s where the conversation tab will appear on web and desktop.</span></span> 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

> [!NOTE]
> <span data-ttu-id="72640-112">Beachten Sie, dass dieses Verhalten nicht auf mobilen Geräten reflektiert wird, da der persönliche bot-Chat bereits über eine dedizierte Stelle in der persönlichen App verfügt.</span><span class="sxs-lookup"><span data-stu-id="72640-112">Note that this behavior is not reflected on mobile since the personal bot chat already has a dedicated place within the personal app.</span></span>

## <a name="moving-the-about-tab"></a><span data-ttu-id="72640-113">Verschieben der Registerkarte "Info"</span><span class="sxs-lookup"><span data-stu-id="72640-113">Moving the “About” tab</span></span>

<span data-ttu-id="72640-114">Auf der Registerkarte "Info" wird standardmäßig immer das Ende der Kopfzeilenleiste der persönlichen App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="72640-114">The “About” tab always defaults to the end of the personal app tab header bar.</span></span> <span data-ttu-id="72640-115">Wenn Sie es an eine andere Position verschieben möchten, müssen Sie die Entitäts-Nr "about" verwenden.</span><span class="sxs-lookup"><span data-stu-id="72640-115">If you wish to move it to another position, you need to use the “about” entityId.</span></span>

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"about",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```
> [!NOTE]
> <span data-ttu-id="72640-116">Beachten Sie, dass die Registerkarte about nicht auf Mobilgeräten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="72640-116">Note that the about tab is not shown on mobile.</span></span>

## <a name="example-code"></a><span data-ttu-id="72640-117">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="72640-117">Example code</span></span>

```json
{
   "staticTabs":[
      {
         "entityId":"homeTab",
         "name":"Home",
         "contentUrl":"https://www.contoso.com",
         "websiteUrl":" https://www.contoso.com ",
         "scopes":[
            "personal"
         ]
      },
      {
         "entityId":"about",
         "scopes":[
            "personal"
         ]
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```
