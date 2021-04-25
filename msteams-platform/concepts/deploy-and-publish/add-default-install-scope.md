---
title: Konfigurieren von Standardinstallationsoptionen für Ihre App
description: Beschreibt, wie Sie die Standardinstallationsoptionen Ihrer App angeben.
ms.topic: how-to
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: a4b70df70c7b9442e29953dae8a8c4e892cb72c1
ms.sourcegitcommit: 7b4f383b506d4bc68a1b5641d6e0f404edbfbc6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2021
ms.locfileid: "51946490"
---
# <a name="add-a-default-install-scope-and-group-capability"></a><span data-ttu-id="584dd-103">Hinzufügen eines Standardinstallationsbereichs und einer Gruppenfunktion</span><span class="sxs-lookup"><span data-stu-id="584dd-103">Add a default install scope and group capability</span></span>

<span data-ttu-id="584dd-104">Es ist üblich, dass eine App mehrere Szenarien in Teams unterstützt, aber Sie haben sie möglicherweise mit einem bestimmten Umfang und einer bestimmten Funktion entworfen.</span><span class="sxs-lookup"><span data-stu-id="584dd-104">It’s common for an app to support multiple scenarios in Teams, but you may have designed it with a specific scope and capability in mind.</span></span> <span data-ttu-id="584dd-105">Wenn Ihre App z. B. hauptsächlich für die Team- oder Kanalnutzung bestimmt ist, können Sie sicherstellen, dass die erste Installationsoption, die Benutzern im Store angezeigt wird, Zu einem Team **hinzufügen ist.**</span><span class="sxs-lookup"><span data-stu-id="584dd-105">For example, if your app is primarily for team or channel use, you can make sure that the first install option users see in the store is **Add to a team**.</span></span>

![Eine App hinzufügen](../../assets/images/compose-extensions/addanapp.png)

<span data-ttu-id="584dd-107">Wenn die primäre Funktion Ihrer App ein Bot ist, können Sie den Bot auch zur Standardfunktion machen, wenn ein Benutzer Ihre App in einem Team installiert.</span><span class="sxs-lookup"><span data-stu-id="584dd-107">If your app's primary capability is a bot, you can also make the bot the default capability when a user installs your app to a team.</span></span> 

## <a name="configure-your-apps-default-install-scope"></a><span data-ttu-id="584dd-108">Konfigurieren des Standardinstallationsbereichs Ihrer App</span><span class="sxs-lookup"><span data-stu-id="584dd-108">Configure your app's default install scope</span></span>

<span data-ttu-id="584dd-109">Konfigurieren Sie den Standardinstallationsbereich für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="584dd-109">Configure the default install scope for your app.</span></span> <span data-ttu-id="584dd-110">Sie können immer nur einen Bereich festlegen.</span><span class="sxs-lookup"><span data-stu-id="584dd-110">You can set only one scope at a time.</span></span>

<span data-ttu-id="584dd-111">**So konfigurieren Sie den Standardinstallationsbereich in Ihrem App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="584dd-111">**To configure the default install scope in your app manifest**</span></span>

1. <span data-ttu-id="584dd-112">Öffnen Sie Ihr App-Manifest, und fügen Sie die Eigenschaft `defaultInstallScope` hinzu.</span><span class="sxs-lookup"><span data-stu-id="584dd-112">Open your app manifest and add the `defaultInstallScope` property.</span></span>
2. <span data-ttu-id="584dd-113">Legen Sie einen Wert von `personal` , , , oder `team` `groupchat` `meetings` (siehe ein Beispiel unten)</span><span class="sxs-lookup"><span data-stu-id="584dd-113">Set a value of `personal`, `team`, `groupchat`, or `meetings` (see an example below).</span></span>

    ```json
    "defaultInstallScope": "meetings",
    ```

> [!NOTE]
> <span data-ttu-id="584dd-114">Weitere Informationen finden Sie im [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="584dd-114">For more information, see the [app manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="configure-the-default-capability-for-shared-scopes"></a><span data-ttu-id="584dd-115">Konfigurieren der Standardfunktion für freigegebene Bereiche</span><span class="sxs-lookup"><span data-stu-id="584dd-115">Configure the default capability for shared scopes</span></span>

<span data-ttu-id="584dd-116">Konfigurieren Sie die Standardfunktion, wenn Ihre App für ein Team, eine Besprechung oder einen Chat installiert ist.</span><span class="sxs-lookup"><span data-stu-id="584dd-116">Configure the default capability when your app is installed for a team, meeting, or chat.</span></span>

<span data-ttu-id="584dd-117">**So konfigurieren Sie Details im App-Manifest**</span><span class="sxs-lookup"><span data-stu-id="584dd-117">**To configure details in app manifest**</span></span>

1. <span data-ttu-id="584dd-118">Öffnen Sie Ihr App-Manifest, und fügen Sie `defaultGroupCapability` die -Eigenschaft hinzu.</span><span class="sxs-lookup"><span data-stu-id="584dd-118">Open your app manifest and add the `defaultGroupCapability` property to it.</span></span>
2. <span data-ttu-id="584dd-119">Speichern Sie die Updates.</span><span class="sxs-lookup"><span data-stu-id="584dd-119">Save the updates.</span></span>

    <span data-ttu-id="584dd-120">Es folgt ein JSON-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="584dd-120">Following is a JSON example:</span></span>

    ```json
    "defaultGroupCapability": {
        "team": "bot",
        "groupchat": "bot",
        "meetings": "tab"
    }
    ```
> [!NOTE]
> <span data-ttu-id="584dd-121">Informationen zum vollständigen Schema finden Sie unter [Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="584dd-121">For information on full schema, see [manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="584dd-122">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="584dd-122">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="584dd-123">Auswählen, wie Ihre App verbreitet werden soll</span><span class="sxs-lookup"><span data-stu-id="584dd-123">Choose how to distribute your app</span></span>](overview.md)
