---
title: Aktivieren der Anpassung Ihrer App
author: heath-hamilton
description: Erfahren Sie, wie Teams Administratoren Ihre App für ihre Organisation anpassen können.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: bf1b43629c87dd4123520c634772e5dea14e0bb5
ms.sourcegitcommit: 64c1cf2a268ef101a519bc31d171618d0f6cd12a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2021
ms.locfileid: "52915083"
---
# <a name="enable-your-microsoft-teams-app-to-be-customized"></a><span data-ttu-id="2c737-103">Aktivieren der anpassungsfähigen Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="2c737-103">Enable your Microsoft Teams app to be customized</span></span>

<span data-ttu-id="2c737-104">Sie können Es Kunden ermöglichen, einige Aspekte Ihrer Microsoft Teams-App im Teams Admin Center anzupassen.</span><span class="sxs-lookup"><span data-stu-id="2c737-104">You can allow customers to customize some aspects of your Microsoft Teams app in the Teams admin center.</span></span> <span data-ttu-id="2c737-105">Dieses Feature wird nur für Apps unterstützt, die im Teams Store veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="2c737-105">This feature is supported only for apps published to the Teams store.</span></span> <span data-ttu-id="2c737-106">Quergeladene Apps und Apps, die für eine Organisation veröffentlicht wurden, können nicht angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="2c737-106">Sideloaded apps and apps published for an org can't be customized.</span></span>

<span data-ttu-id="2c737-107">Einige mögliche Beispiele für dieses Feature sind:</span><span class="sxs-lookup"><span data-stu-id="2c737-107">Some possible examples of this feature include:</span></span>

* <span data-ttu-id="2c737-108">Ändern der Akzentfarbe der App entsprechend der Marke einer Organisation.</span><span class="sxs-lookup"><span data-stu-id="2c737-108">Changing the app's accent color to match an org's brand.</span></span>
* <span data-ttu-id="2c737-109">Aktualisieren des App-Namens von *Contoso* auf *Contoso-Agent*, bei dem es sich um den Namen handelt, der Benutzern in der Organisation angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2c737-109">Updating the app name from *Contoso* to *Contoso Agent*, which is the name users in the org will see.</span></span> <span data-ttu-id="2c737-110">(Hinweis: Benutzern, die einen Connector zu einem Chat oder Kanal hinzufügen, wird weiterhin der ursprüngliche App-Name *Contoso* angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="2c737-110">(Note: Users adding a connector to a chat or a channel will still see the original app name, *Contoso*.)</span></span>

<span data-ttu-id="2c737-111">Sie können dieses Feature im [Entwicklerportal für Teams](https://dev.teams.microsoft.com/home)aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2c737-111">You can enable this feature in the [Developer Portal for Teams](https://dev.teams.microsoft.com/home).</span></span> <span data-ttu-id="2c737-112">Dadurch `configurableProperties` wird konfiguriert, welche in Versionen vor 1.10 des Teams-App-Manifests nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2c737-112">This configures `configurableProperties`, which aren't available in versions prior to 1.10 of the Teams app manifest.</span></span>

## <a name="test-your-app"></a><span data-ttu-id="2c737-113">Testen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="2c737-113">Test your app</span></span>

<span data-ttu-id="2c737-114">Sie können dieses Feature während der Entwicklung nicht testen.</span><span class="sxs-lookup"><span data-stu-id="2c737-114">You cannot test this feature during development.</span></span> <span data-ttu-id="2c737-115">Die App-Anpassung wird beim Querladen oder Veröffentlichen im App-Katalog einer Organisation nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2c737-115">App customization is not supported for sideloading or publishing to an organization's app catalog.</span></span>

## <a name="user-considerations"></a><span data-ttu-id="2c737-116">Überlegungen zu Benutzern</span><span class="sxs-lookup"><span data-stu-id="2c737-116">User considerations</span></span>

<span data-ttu-id="2c737-117">Stellen Sie als App-Herausgeber die folgenden Informationen für Kunden in Teams Administratoren bereit:</span><span class="sxs-lookup"><span data-stu-id="2c737-117">As the app publisher, provide the following information to customers in Teams admins:</span></span>
* <span data-ttu-id="2c737-118">Fügen Sie einen Hinweis ein, in dem empfohlen wird, Anpassungsänderungen in einem Teams Testmandanten zu testen, bevor Sie Änderungen in der Produktionsumgebung vornehmen.</span><span class="sxs-lookup"><span data-stu-id="2c737-118">Include a note recommending to test customization changes in a Teams test tenant before making changes in their production environment.</span></span> 
* <span data-ttu-id="2c737-119">Stellen Sie bewährte Methoden zum Anpassen Ihrer App bereit.</span><span class="sxs-lookup"><span data-stu-id="2c737-119">Provide best practices for how to customize your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c737-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2c737-120">See also</span></span>

* [<span data-ttu-id="2c737-121">Anpassen von Apps im Teams Admin Center</span><span class="sxs-lookup"><span data-stu-id="2c737-121">Customize apps in the Teams admin center</span></span>](/MicrosoftTeams/customize-apps)
