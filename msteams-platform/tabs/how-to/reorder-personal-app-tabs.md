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
# <a name="reorder-personal-app-tabs"></a>Neuanordnen von Tabs für persönliche apps

Beginnend mit manifestVersion 1,7 können Entwickler alle Registerkarten in Ihrer persönlichen APP neu anordnen. Insbesondere kann ein Entwickler die Registerkarte "bot Chat" (die immer auf die erste Position eingestellt ist) an einer beliebigen Stelle in der Kopfzeile der persönlichen App-Registerkarte verschieben. Wir haben zwei reservierte Registerkarten Entität-Schlüsselwörter deklariert: "Unterhaltungen" und "about".

## <a name="moving-the-chatconversation-tab"></a>Verschieben der Registerkarte "Chat/Unterhaltung"

Wenn Sie einen bot mit einem "persönlichen" Bereich erstellen, wird er immer an der ersten Registerkarten Position in einer persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie dem Manifest ein statisches Tab-Objekt mit dem reservierten Schlüsselwort "Conversations" hinzufügen. Überall dort, wo Sie die Registerkarte "Unterhaltungen" im Array "staticTabs" hinzufügen, wird die Registerkarte Unterhaltung auf dem Bildschirm "Internet" und "Desktop" angezeigt. 

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
> Beachten Sie, dass dieses Verhalten nicht auf mobilen Geräten reflektiert wird, da der persönliche bot-Chat bereits über eine dedizierte Stelle in der persönlichen App verfügt.

## <a name="moving-the-about-tab"></a>Verschieben der Registerkarte "Info"

Auf der Registerkarte "Info" wird standardmäßig immer das Ende der Kopfzeilenleiste der persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie die Entitäts-Nr "about" verwenden.

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
> Beachten Sie, dass die Registerkarte about nicht auf Mobilgeräten angezeigt wird.

## <a name="example-code"></a>Beispielcode

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
