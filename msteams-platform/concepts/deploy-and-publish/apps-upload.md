---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in einem Microsoft Teams. Das Querladen ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: 39e94317ceb615ecd7d5481276ffafed5afe5cde
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565193"
---
# <a name="upload-your-app-in-microsoft-teams"></a><span data-ttu-id="44935-104">Hochladen Ihrer App in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="44935-104">Upload your app in Microsoft Teams</span></span>

<span data-ttu-id="44935-105">Sie können apps querladen Microsoft Teams, ohne sie in Ihrer Organisation oder im Teams veröffentlichen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="44935-105">You can sideload Microsoft Teams apps without having to publish to your organization or the Teams store.</span></span> <span data-ttu-id="44935-106">Dies ist in den folgenden Szenarien sinnvoll:</span><span class="sxs-lookup"><span data-stu-id="44935-106">This makes sense in the following scenarios:</span></span>

* <span data-ttu-id="44935-107">Sie möchten eine App lokal selbst oder mit anderen Entwicklern testen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="44935-107">You want to test and debug an app locally yourself or with other developers.</span></span>
* <span data-ttu-id="44935-108">Sie haben eine App nur für sich selbst erstellt.</span><span class="sxs-lookup"><span data-stu-id="44935-108">You built an app just for yourself.</span></span> <span data-ttu-id="44935-109">Zum Beispiel, um einen Workflow zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="44935-109">For example, to automate a workflow.</span></span>
* <span data-ttu-id="44935-110">Sie haben eine App für eine kleine Gruppe von Benutzern, z. B. Ihre Arbeitsgruppe, erstellt.</span><span class="sxs-lookup"><span data-stu-id="44935-110">You built an app for a small set of users, such as, your work group.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44935-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="44935-111">Prerequisites</span></span>

* <span data-ttu-id="44935-112">Erstellen Sie Ihr [App-Paket,](~/concepts/build-and-test/apps-package.md) [und überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="44935-112">Create your [app package](~/concepts/build-and-test/apps-package.md) and [validate it](https://dev.teams.microsoft.com/appvalidation.html) for errors.</span></span>
* <span data-ttu-id="44935-113">[Aktivieren Sie das Hochladen benutzerdefinierter](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Teams.</span><span class="sxs-lookup"><span data-stu-id="44935-113">[Enable custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.</span></span>
* <span data-ttu-id="44935-114">Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs darauf zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="44935-114">Make sure that your app is running and accessible via HTTPs.</span></span>

## <a name="upload-your-app"></a><span data-ttu-id="44935-115">Hochladen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="44935-115">Upload your app</span></span>

<span data-ttu-id="44935-116">Sie können Ihre App in abhängigkeit davon, wie Sie den Bereich Ihrer App konfiguriert haben, in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen.</span><span class="sxs-lookup"><span data-stu-id="44935-116">You can sideload your app to a team, chat, meeting, or for personal use depending on how you configured your app's scope.</span></span>

1. <span data-ttu-id="44935-117">Melden Sie sich beim Teams-Client mit Ihrem [Microsoft 365 an.](~/build-your-first-app/build-and-run.md#prerequisites)</span><span class="sxs-lookup"><span data-stu-id="44935-117">Log in to the Teams client with your [Microsoft 365 development account](~/build-your-first-app/build-and-run.md#prerequisites).</span></span>
1. <span data-ttu-id="44935-118">Wählen **Sie Apps** und Hochladen eine **benutzerdefinierte App aus.**</span><span class="sxs-lookup"><span data-stu-id="44935-118">Select **Apps** and choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="44935-119">Wählen Sie Ihr App-.zip aus.</span><span class="sxs-lookup"><span data-stu-id="44935-119">Select your app package .zip file.</span></span> <span data-ttu-id="44935-120">Ein Installationsdialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="44935-120">An install dialog displays.</span></span>
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot mit einem Beispiel für ein Teams-App-Installationsdialogfeld.":::
1. <span data-ttu-id="44935-122">Fügen Sie Ihre App zu Teams.</span><span class="sxs-lookup"><span data-stu-id="44935-122">Add your app to Teams.</span></span>

## <a name="troubleshoot-upload-issues"></a><span data-ttu-id="44935-123">Behandeln von Problemen beim Hochladen</span><span class="sxs-lookup"><span data-stu-id="44935-123">Troubleshoot upload issues</span></span>

<span data-ttu-id="44935-124">Wenn ihre App nicht querladen kann, gehen Sie wie folgt vor, bis das Problem behoben ist:</span><span class="sxs-lookup"><span data-stu-id="44935-124">If your app fails to sideload, do the following until the issue resolves:</span></span>

1. <span data-ttu-id="44935-125">Gehen Sie zurück durch die Anweisungen zum [Erstellen Ihres App-Pakets.](../../concepts/build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="44935-125">Go back through the instructions for [creating your app package](../../concepts/build-and-test/apps-package.md).</span></span>
1. <span data-ttu-id="44935-126">[Überprüfen Sie Ihr App-Paket](https://dev.teams.microsoft.com/appvalidation.html) erneut.</span><span class="sxs-lookup"><span data-stu-id="44935-126">[Validate your app package](https://dev.teams.microsoft.com/appvalidation.html) again.</span></span>
1. <span data-ttu-id="44935-127">Stellen Sie sicher, dass Ihr App-Manifest dem neuesten Schema [entspricht.](../../resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="44935-127">Make sure your app manifest matches the latest [schema](../../resources/schema/manifest-schema.md).</span></span>

## <a name="access-your-app"></a><span data-ttu-id="44935-128">Zugreifen auf Ihre App</span><span class="sxs-lookup"><span data-stu-id="44935-128">Access your app</span></span>

<span data-ttu-id="44935-129">Teams bietet verschiedene Möglichkeiten zum Öffnen von Apps.</span><span class="sxs-lookup"><span data-stu-id="44935-129">Teams provides several ways to open apps.</span></span> <span data-ttu-id="44935-130">Weitere Informationen finden Sie unter [Zugreifen auf Ihre Apps in Teams.](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a)</span><span class="sxs-lookup"><span data-stu-id="44935-130">For more information, see [access your apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).</span></span>

## <a name="update-your-app"></a><span data-ttu-id="44935-131">Aktualisieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="44935-131">Update your app</span></span>

<span data-ttu-id="44935-132">Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widergespiegelt).</span><span class="sxs-lookup"><span data-stu-id="44935-132">You don't have to sideload your app again if you make code changes (these are reflected in Teams in real-time).</span></span> <span data-ttu-id="44935-133">Sie müssen jedoch neu installieren, wenn Sie app-Konfigurationen ändern.</span><span class="sxs-lookup"><span data-stu-id="44935-133">However, you must reinstall if you change any app configurations.</span></span>

## <a name="remove-your-app"></a><span data-ttu-id="44935-134">Entfernen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="44935-134">Remove your app</span></span>

<span data-ttu-id="44935-135">Klicken Sie zum Entfernen Ihrer App mit der rechten Maustaste auf das Teams und **wählen Sie Deinstallieren aus.**</span><span class="sxs-lookup"><span data-stu-id="44935-135">To remove your app, right click the app icon in Teams and select **Uninstall**.</span></span>

> [!NOTE]
> <span data-ttu-id="44935-136">Persönliche Botaktivitäten können nicht vollständig entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="44935-136">You can't remove personal bot activity entirely.</span></span> <span data-ttu-id="44935-137">Wenn Sie die App entfernen und erneut hinzufügen, wird die neue Kommunikation mit dem Bot an die vorherige Unterhaltung angefügt.</span><span class="sxs-lookup"><span data-stu-id="44935-137">If you remove the app and add it again, new communication with the bot appends to the previous conversation with it.</span></span>

## <a name="next-step"></a><span data-ttu-id="44935-138">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="44935-138">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="44935-139">Verwenden Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="44935-139">Use your Teams app</span></span>](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
