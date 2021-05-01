---
title: Hochladen Ihrer benutzerdefinierten App
description: Erfahren Sie, wie Sie Ihre App in einem Microsoft Teams. Das Querladen ist beim Testen und Debuggen einer App während der Entwicklung üblich.
ms.topic: how-to
author: KirtiPereira
ms.author: surbhigupta
ms.openlocfilehash: a82f7d6498db4cceb69f1b7f5ff53b1646371ce8
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101569"
---
# <a name="upload-your-app-in-microsoft-teams"></a><span data-ttu-id="d5a72-104">Hochladen Ihrer App in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d5a72-104">Upload your app in Microsoft Teams</span></span>

<span data-ttu-id="d5a72-105">Sie können apps querladen Microsoft Teams, ohne sie in Ihrer Organisation oder im Teams veröffentlichen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="d5a72-105">You can sideload Microsoft Teams apps without having to publish to your organization or the Teams store.</span></span> <span data-ttu-id="d5a72-106">Dies ist in den folgenden Szenarien sinnvoll:</span><span class="sxs-lookup"><span data-stu-id="d5a72-106">This makes sense in the following scenarios:</span></span>

* <span data-ttu-id="d5a72-107">Sie möchten eine App lokal selbst oder mit anderen Entwicklern testen und debuggen.</span><span class="sxs-lookup"><span data-stu-id="d5a72-107">You want to test and debug an app locally yourself or with other developers.</span></span>
* <span data-ttu-id="d5a72-108">Sie haben eine App nur für sich selbst erstellt (z. B. zum Automatisieren eines Workflows).</span><span class="sxs-lookup"><span data-stu-id="d5a72-108">You built an app just for yourself (for example, to automate a workflow).</span></span>
* <span data-ttu-id="d5a72-109">Sie haben eine App für eine kleine Gruppe von Benutzern (z. B. Ihre Arbeitsgruppe) erstellt.</span><span class="sxs-lookup"><span data-stu-id="d5a72-109">You built an app for a small set of users (such as your work group).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d5a72-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="d5a72-110">Prerequisites</span></span>

* <span data-ttu-id="d5a72-111">Erstellen Sie Ihr [App-Paket,](~/concepts/build-and-test/apps-package.md) [und überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.</span><span class="sxs-lookup"><span data-stu-id="d5a72-111">Create your [app package](~/concepts/build-and-test/apps-package.md) and [validate it](https://dev.teams.microsoft.com/appvalidation.html) for errors.</span></span>
* <span data-ttu-id="d5a72-112">[Aktivieren Sie das Hochladen benutzerdefinierter](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Teams.</span><span class="sxs-lookup"><span data-stu-id="d5a72-112">[Enable custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.</span></span>
* <span data-ttu-id="d5a72-113">Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs darauf zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="d5a72-113">Make sure that your app is running and accessible via HTTPs.</span></span>

## <a name="upload-your-app"></a><span data-ttu-id="d5a72-114">Hochladen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="d5a72-114">Upload your app</span></span>

<span data-ttu-id="d5a72-115">Sie können Ihre App in abhängigkeit davon, wie Sie den Bereich Ihrer App konfiguriert haben, in ein Team, einen Chat, eine Besprechung oder zur persönlichen Verwendung querladen.</span><span class="sxs-lookup"><span data-stu-id="d5a72-115">You can sideload your app to a team, chat, meeting, or for personal use depending on how you configured your app's scope.</span></span>

1. <span data-ttu-id="d5a72-116">Melden Sie sich beim Teams-Client mit Ihrem [Microsoft 365 an.](~/build-your-first-app/build-and-run.md#prerequisites)</span><span class="sxs-lookup"><span data-stu-id="d5a72-116">Log in to the Teams client with your [Microsoft 365 development account](~/build-your-first-app/build-and-run.md#prerequisites).</span></span>
1. <span data-ttu-id="d5a72-117">Wählen **Sie Apps** und Hochladen eine **benutzerdefinierte App aus.**</span><span class="sxs-lookup"><span data-stu-id="d5a72-117">Select **Apps** and choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="d5a72-118">Wählen Sie Ihr App-.zip aus.</span><span class="sxs-lookup"><span data-stu-id="d5a72-118">Select your app package .zip file.</span></span> <span data-ttu-id="d5a72-119">Ein Installationsdialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d5a72-119">An install dialog displays.</span></span>
:::image type="content" source="~/assets/images/build-your-first-app/add-teams-app.png" alt-text="Screenshot mit einem Beispiel für ein Teams-App-Installationsdialogfeld.":::
1. <span data-ttu-id="d5a72-121">Fügen Sie Ihre App zu Teams.</span><span class="sxs-lookup"><span data-stu-id="d5a72-121">Add your app to Teams.</span></span>

## <a name="troubleshoot-upload-issues"></a><span data-ttu-id="d5a72-122">Behandeln von Problemen beim Hochladen</span><span class="sxs-lookup"><span data-stu-id="d5a72-122">Troubleshoot upload issues</span></span>

<span data-ttu-id="d5a72-123">Wenn ihre App nicht querladen kann, gehen Sie wie folgt vor, bis das Problem behoben ist:</span><span class="sxs-lookup"><span data-stu-id="d5a72-123">If your app fails to sideload, do the following until the issue resolves:</span></span>

1. <span data-ttu-id="d5a72-124">Gehen Sie zurück durch die Anweisungen zum [Erstellen Ihres App-Pakets.](../../concepts/build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="d5a72-124">Go back through the instructions for [creating your app package](../../concepts/build-and-test/apps-package.md).</span></span>
1. <span data-ttu-id="d5a72-125">[Überprüfen Sie Ihr App-Paket](https://dev.teams.microsoft.com/appvalidation.html) erneut.</span><span class="sxs-lookup"><span data-stu-id="d5a72-125">[Validate your app package](https://dev.teams.microsoft.com/appvalidation.html) again.</span></span>
1. <span data-ttu-id="d5a72-126">Stellen Sie sicher, dass Ihr App-Manifest dem neuesten Schema [entspricht.](../../resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="d5a72-126">Make sure your app manifest matches the latest [schema](../../resources/schema/manifest-schema.md).</span></span>

## <a name="access-your-app"></a><span data-ttu-id="d5a72-127">Zugreifen auf Ihre App</span><span class="sxs-lookup"><span data-stu-id="d5a72-127">Access your app</span></span>

<span data-ttu-id="d5a72-128">Teams bietet verschiedene Möglichkeiten zum Öffnen von Apps.</span><span class="sxs-lookup"><span data-stu-id="d5a72-128">Teams provides several ways to open apps.</span></span> <span data-ttu-id="d5a72-129">Weitere Informationen finden Sie unter [Zugreifen auf Ihre Apps in Teams.](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a)</span><span class="sxs-lookup"><span data-stu-id="d5a72-129">For more information, see [access your apps in Teams](https://support.microsoft.com/office/access-your-apps-in-teams-0758cb09-9e85-40e7-a974-51df7734646a).</span></span>

## <a name="update-your-app"></a><span data-ttu-id="d5a72-130">Aktualisieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="d5a72-130">Update your app</span></span>

<span data-ttu-id="d5a72-131">Sie müssen Ihre App nicht erneut querladen, wenn Sie Codeänderungen vornehmen (diese werden in Teams in Echtzeit widergespiegelt).</span><span class="sxs-lookup"><span data-stu-id="d5a72-131">You don't have to sideload your app again if you make code changes (these are reflected in Teams in real-time).</span></span> <span data-ttu-id="d5a72-132">Sie müssen jedoch neu installieren, wenn Sie app-Konfigurationen ändern.</span><span class="sxs-lookup"><span data-stu-id="d5a72-132">However, you must reinstall if you change any app configurations.</span></span>

## <a name="remove-your-app"></a><span data-ttu-id="d5a72-133">Entfernen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="d5a72-133">Remove your app</span></span>

<span data-ttu-id="d5a72-134">Klicken Sie zum Entfernen Ihrer App mit der rechten Maustaste auf das Teams und **wählen Sie Deinstallieren aus.**</span><span class="sxs-lookup"><span data-stu-id="d5a72-134">To remove your app, right click the app icon in Teams and select **Uninstall**.</span></span>

> [!NOTE]
> <span data-ttu-id="d5a72-135">Persönliche Botaktivitäten können nicht vollständig entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="d5a72-135">You can't remove personal bot activity entirely.</span></span> <span data-ttu-id="d5a72-136">Wenn Sie die App entfernen und erneut hinzufügen, wird die neue Kommunikation mit dem Bot an die vorherige Unterhaltung angefügt.</span><span class="sxs-lookup"><span data-stu-id="d5a72-136">If you remove the app and add it again, new communication with the bot appends to the previous conversation with it.</span></span>

## <a name="next-step"></a><span data-ttu-id="d5a72-137">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="d5a72-137">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d5a72-138">Verwenden Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="d5a72-138">Use your Teams app</span></span>](https://support.microsoft.com/office/apps-and-services-cc1fba57-9900-4634-8306-2360a40c665b?ui=en-us&rs=en-us&ad=us)
