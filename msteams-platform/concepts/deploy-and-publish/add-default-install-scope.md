---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Sie die Standardinstallationsoptionen Ihrer App angeben.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: 561a4f2910e703db5ffce6176f6177dfd661d2ce
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230932"
---
# <a name="configure-default-install-options-for-your-microsoft-teams-app"></a><span data-ttu-id="117e7-103">Konfigurieren von Standardinstallationsoptionen für Ihre Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="117e7-103">Configure default install options for your Microsoft Teams app</span></span>

<span data-ttu-id="117e7-104">Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Umfang und einer bestimmten Funktion entworfen.</span><span class="sxs-lookup"><span data-stu-id="117e7-104">It’s common for an app to support multiple scenarios in Teams, but you may have designed it with a specific scope and capability in mind.</span></span> <span data-ttu-id="117e7-105">Wenn Ihre App z. B. hauptsächlich für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, Zu einem Team **hinzufügen ist.**</span><span class="sxs-lookup"><span data-stu-id="117e7-105">For example, if your app is primarily for team or channel use, you can make sure that the first install option users see in the store is **Add to a team**.</span></span>

:::row:::
   :::column span="2":::

![Hinzufügen eines App-Dropdownbeispiels](../../assets/images/compose-extensions/addanapp.png)

   :::column-end:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

<span data-ttu-id="117e7-107">Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.</span><span class="sxs-lookup"><span data-stu-id="117e7-107">If your app's primary capability is a bot, you can also make the bot the default capability when a user installs your app to a team.</span></span>

## <a name="configure-your-apps-default-install-scope"></a><span data-ttu-id="117e7-108">Konfigurieren des Standardinstallationsbereichs Ihrer App</span><span class="sxs-lookup"><span data-stu-id="117e7-108">Configure your app's default install scope</span></span>

<span data-ttu-id="117e7-109">Konfigurieren Sie den Standardinstallationsbereich für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="117e7-109">Configure the default install scope for your app.</span></span> <span data-ttu-id="117e7-110">Sie können immer nur einen Bereich festlegen.</span><span class="sxs-lookup"><span data-stu-id="117e7-110">You can set only one scope at a time.</span></span>

<span data-ttu-id="117e7-111">**So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="117e7-111">**To configure the default install scope in your app manifest**</span></span>

1. <span data-ttu-id="117e7-112">Öffnen Sie Ihr App-Manifest, und fügen Sie die Eigenschaft `defaultInstallScope` hinzu.</span><span class="sxs-lookup"><span data-stu-id="117e7-112">Open your app manifest and add the `defaultInstallScope` property.</span></span>
2. <span data-ttu-id="117e7-113">Legen Sie den Standardinstallationsbereichswert als `personal` , `team` , oder `groupchat` . `meetings`</span><span class="sxs-lookup"><span data-stu-id="117e7-113">Set default install scope value as, either `personal`, `team`, `groupchat`, or `meetings`.</span></span>

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> <span data-ttu-id="117e7-114">Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="117e7-114">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="configure-the-default-capability-for-shared-scopes"></a><span data-ttu-id="117e7-115">Konfigurieren der Standardfunktion für freigegebene Bereiche</span><span class="sxs-lookup"><span data-stu-id="117e7-115">Configure the default capability for shared scopes</span></span>

<span data-ttu-id="117e7-116">Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder einen Gruppenchat installiert ist.</span><span class="sxs-lookup"><span data-stu-id="117e7-116">Configure the default capability when your app is installed for a team, meeting, or groupchat.</span></span>

> [!NOTE]
> <span data-ttu-id="117e7-117">`defaultGroupCapability` bietet die Standardfunktion, die dem Team, dem Groupchat oder der Besprechung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="117e7-117">`defaultGroupCapability` provides the default capability that will be added to the team, groupchat, or meeting.</span></span> <span data-ttu-id="117e7-118">Wählen Sie eine Registerkarte, einen Bot oder einen Connector als Standardfunktion für Ihre App aus, Sie müssen jedoch sicherstellen, dass Sie die ausgewählte Funktion in Ihrer App-Definition bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="117e7-118">Select a tab, bot, or connector as the default capability for your app, but you must ensure that you have provided the selected capability in your app definition.</span></span>

<span data-ttu-id="117e7-119">**So konfigurieren Sie Details im App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="117e7-119">**To configure details in app manifest**</span></span>

1. <span data-ttu-id="117e7-120">Öffnen Sie Ihr App-Manifest, und fügen Sie `defaultGroupCapability` die -Eigenschaft hinzu.</span><span class="sxs-lookup"><span data-stu-id="117e7-120">Open your app manifest and add the `defaultGroupCapability` property to it.</span></span>
2. <span data-ttu-id="117e7-121">Legen Sie den Wert `team` , `groupchat` oder . `meetings`</span><span class="sxs-lookup"><span data-stu-id="117e7-121">Set a value of `team`, `groupchat`, or `meetings`.</span></span>
3. <span data-ttu-id="117e7-122">Für die ausgewählte Gruppenfunktion sind die verfügbaren Gruppenfunktionen , `bot` `tab` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="117e7-122">For the selected group capability, the available group capabilities are, `bot`, `tab`, or `connector`.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="117e7-123">Sie können nur eine Standardfunktion, `bot` , , oder für die ausgewählte `tab` `connector` Gruppenfunktion auswählen.</span><span class="sxs-lookup"><span data-stu-id="117e7-123">You can select only one default capability, `bot`, `tab`, or `connector` for the selected group capability.</span></span>

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```

> [!NOTE]
> <span data-ttu-id="117e7-124">Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="117e7-124">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="117e7-125">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="117e7-125">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="117e7-126">Erstellen Ihres App-Pakets</span><span class="sxs-lookup"><span data-stu-id="117e7-126">Create your app package</span></span>](~/concepts/build-and-test/apps-package.md)
