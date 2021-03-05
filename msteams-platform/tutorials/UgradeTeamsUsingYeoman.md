---
title: Lernprogramm – Aktualisieren von Teams mithilfe des Microsoft Teams Yeoman-Generators
description: Erfahren Sie, wie Sie den Microsoft Teams Yeoman-Generator zum Upgraden von Teams verwenden.
ms.topic: tutorial
ms.openlocfilehash: 0c52dd15703000a1c0f99ddd28401dd686e1b1bb
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449610"
---
# <a name="upgrade-teams-using-microsoft-teams-yeoman-generator"></a><span data-ttu-id="4074e-103">Aktualisieren von Teams mithilfe des Microsoft Teams Yeoman-Generators</span><span class="sxs-lookup"><span data-stu-id="4074e-103">Upgrade Teams using Microsoft Teams Yeoman generator</span></span>
<span data-ttu-id="4074e-104">Dieses Lernprogramm hilft Ihnen, Ihre aktuelle Microsoft Teams-App-Version mithilfe des Microsoft Teams Yeoman-Generators auf die neueste Version zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4074e-104">This tutorial helps you to upgrade your current Microsoft Teams app version to the latest version using the Microsoft Teams Yeoman generator.</span></span>

## <a name="get-current-version-of-teams"></a><span data-ttu-id="4074e-105">Aktuelle Version von Teams erhalten</span><span class="sxs-lookup"><span data-stu-id="4074e-105">Get current version of Teams</span></span>
```PowerShell
 yo teams --version
```

## <a name="update-teams"></a><span data-ttu-id="4074e-106">Aktualisieren von Teams</span><span class="sxs-lookup"><span data-stu-id="4074e-106">Update Teams</span></span>
<span data-ttu-id="4074e-107">Der yo-Befehl listet verschiedene Optionen auf, die vom Erstellen eines Projekts bis zum Aktualisieren des Generators reichen.</span><span class="sxs-lookup"><span data-stu-id="4074e-107">The yo command lists out various options ranging from creating project to updating generator.</span></span> <span data-ttu-id="4074e-108">Verwenden Sie den folgenden Befehl, um den Aktualisierungsgenerator auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4074e-108">Use the following command to select update generator:</span></span>
```PowerShell
 yo
```

<span data-ttu-id="4074e-109">Verwenden Sie die Pfeiltasten, um **Update Generators zu wählen.**</span><span class="sxs-lookup"><span data-stu-id="4074e-109">Use the arrow keys to choose **Update Generators**.</span></span>
<span data-ttu-id="4074e-110">![Bild von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)</span><span class="sxs-lookup"><span data-stu-id="4074e-110">![image of YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)</span></span>

<span data-ttu-id="4074e-111">In der Liste werden alle verfügbaren Generatoren angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4074e-111">The list displays all the available generators.</span></span> <span data-ttu-id="4074e-112">Verwenden Sie zum Auswählen oder Aufheben der Auswahl der Teams-Version aus den verfügbaren Optionen die **Leerraumleiste,** und wählen Sie einen bestimmten Generator aus.</span><span class="sxs-lookup"><span data-stu-id="4074e-112">To select or unselect Teams version from the available options, use the **space bar** and choose a specific generator.</span></span>
<span data-ttu-id="4074e-113">![Abbildung von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)</span><span class="sxs-lookup"><span data-stu-id="4074e-113">![image of UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)</span></span>

<span data-ttu-id="4074e-114">Es dauert einige Sekunden bis Minuten, bis die Installation von Teams abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="4074e-114">It takes few seconds to minutes for Teams installation to complete.</span></span>

<span data-ttu-id="4074e-115">Verwenden Sie nach Abschluss der Installation den folgenden Befehl, um die installierte Version zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="4074e-115">After the installation is complete, use the following command to check the installed version:</span></span>

```PowerShell
yo teams --version
```

![Abbildung von FindVersionAfterInstallation](~/assets/images/Update-Teams/FindVersionAfterInstallation.png)

<span data-ttu-id="4074e-117">Congrat!</span><span class="sxs-lookup"><span data-stu-id="4074e-117">Congrats!</span></span> <span data-ttu-id="4074e-118">Sie haben Microsoft Teams aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="4074e-118">You have upgraded Microsoft Teams.</span></span>

