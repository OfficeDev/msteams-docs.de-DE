---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Sie die Standardinstallationsoptionen Ihrer App angeben.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 0afcce50a4779421016c23c4ec4e3d25cc3401d1
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058614"
---
# <a name="add-a-default-install-scope-and-group-capability"></a><span data-ttu-id="8ced3-103">Hinzufügen eines Standardinstallationsbereichs und einer Gruppenfunktion</span><span class="sxs-lookup"><span data-stu-id="8ced3-103">Add a default install scope and group capability</span></span>

<span data-ttu-id="8ced3-104">Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Umfang und einer bestimmten Funktion entworfen.</span><span class="sxs-lookup"><span data-stu-id="8ced3-104">It’s common for an app to support multiple scenarios in Teams, but you may have designed it with a specific scope and capability in mind.</span></span> <span data-ttu-id="8ced3-105">Wenn Ihre App z. B. hauptsächlich für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, Zu einem Team **hinzufügen ist.**</span><span class="sxs-lookup"><span data-stu-id="8ced3-105">For example, if your app is primarily for team or channel use, you can make sure that the first install option users see in the store is **Add to a team**.</span></span>

![Eine App hinzufügen](../../assets/images/compose-extensions/addanapp.png)

<span data-ttu-id="8ced3-107">Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.</span><span class="sxs-lookup"><span data-stu-id="8ced3-107">If your app's primary capability is a bot, you can also make the bot the default capability when a user installs your app to a team.</span></span>

## <a name="configure-your-apps-default-install-scope"></a><span data-ttu-id="8ced3-108">Konfigurieren des Standardinstallationsbereichs Ihrer App</span><span class="sxs-lookup"><span data-stu-id="8ced3-108">Configure your app's default install scope</span></span>

<span data-ttu-id="8ced3-109">Konfigurieren Sie den Standardinstallationsbereich für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="8ced3-109">Configure the default install scope for your app.</span></span> <span data-ttu-id="8ced3-110">Sie können immer nur einen Bereich festlegen.</span><span class="sxs-lookup"><span data-stu-id="8ced3-110">You can set only one scope at a time.</span></span>

<span data-ttu-id="8ced3-111">**So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="8ced3-111">**To configure the default install scope in your app manifest**</span></span>

1. <span data-ttu-id="8ced3-112">Öffnen Sie Ihr App-Manifest, und fügen Sie die Eigenschaft `defaultInstallScope` hinzu.</span><span class="sxs-lookup"><span data-stu-id="8ced3-112">Open your app manifest and add the `defaultInstallScope` property.</span></span>
2. <span data-ttu-id="8ced3-113">Legen Sie den Standardinstallationsbereichswert als `personal` , `team` , oder `groupchat` . `meetings`</span><span class="sxs-lookup"><span data-stu-id="8ced3-113">Set default install scope value as, either `personal`, `team`, `groupchat`, or `meetings`.</span></span>

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> <span data-ttu-id="8ced3-114">Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="8ced3-114">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="configure-the-default-capability-for-shared-scopes"></a><span data-ttu-id="8ced3-115">Konfigurieren der Standardfunktion für freigegebene Bereiche</span><span class="sxs-lookup"><span data-stu-id="8ced3-115">Configure the default capability for shared scopes</span></span>

<span data-ttu-id="8ced3-116">Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder einen Gruppenchat installiert ist.</span><span class="sxs-lookup"><span data-stu-id="8ced3-116">Configure the default capability when your app is installed for a team, meeting, or groupchat.</span></span>

> [!NOTE]
> <span data-ttu-id="8ced3-117">`defaultGroupCapability` bietet die Standardfunktion, die dem Team, dem Groupchat oder der Besprechung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8ced3-117">`defaultGroupCapability` provides the default capability that will be added to the team, groupchat, or meeting.</span></span> <span data-ttu-id="8ced3-118">Wählen Sie eine Registerkarte, einen Bot oder einen Connector als Standardfunktion für Ihre App aus, Sie müssen jedoch sicherstellen, dass Sie die ausgewählte Funktion in Ihrer App-Definition bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="8ced3-118">Select a tab, bot, or connector as the default capability for your app, but you must ensure that you have provided the selected capability in your app definition.</span></span>

<span data-ttu-id="8ced3-119">**So konfigurieren Sie Details im App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="8ced3-119">**To configure details in app manifest**</span></span>

1. <span data-ttu-id="8ced3-120">Öffnen Sie Ihr App-Manifest, und fügen Sie `defaultGroupCapability` die -Eigenschaft hinzu.</span><span class="sxs-lookup"><span data-stu-id="8ced3-120">Open your app manifest and add the `defaultGroupCapability` property to it.</span></span>
2. <span data-ttu-id="8ced3-121">Legen Sie den Wert `team` , `groupchat` oder . `meetings`</span><span class="sxs-lookup"><span data-stu-id="8ced3-121">Set a value of `team`, `groupchat`, or `meetings`.</span></span>
3. <span data-ttu-id="8ced3-122">Für die ausgewählte Gruppenfunktion sind die verfügbaren Gruppenfunktionen , `bot` `tab` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="8ced3-122">For the selected group capability, the available group capabilities are, `bot`, `tab`, or `connector`.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="8ced3-123">Sie können nur eine Standardfunktion, `bot` , , oder für die ausgewählte `tab` `connector` Gruppenfunktion auswählen.</span><span class="sxs-lookup"><span data-stu-id="8ced3-123">You can select only one default capability, `bot`, `tab`, or `connector` for the selected group capability.</span></span>

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> <span data-ttu-id="8ced3-124">Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="8ced3-124">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="8ced3-125">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8ced3-125">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ced3-126">Auswählen, wie Ihre App verbreitet werden soll</span><span class="sxs-lookup"><span data-stu-id="8ced3-126">Choose how to distribute your app</span></span>](overview.md)
