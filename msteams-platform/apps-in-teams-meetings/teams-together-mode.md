---
title: Szenen im benutzerdefinierten Modus "Zusammen"
description: Arbeiten mit benutzerdefinierten Szenen im Zusammen-Modus
ms.topic: conceptual
ms.openlocfilehash: 74405041c6d90c2ef502a2c52570650daebb3526
ms.sourcegitcommit: d354ab3cda83e6cd8bb9f03bc0fa2d1c1a61a6ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "53463324"
---
# <a name="custom-together-mode-scenes-in-teams"></a><span data-ttu-id="1f918-103">Benutzerdefinierte Zusammen-Modus-Szenen</span><span class="sxs-lookup"><span data-stu-id="1f918-103">Custom Together Mode scenes in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="1f918-104">Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1f918-104">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="1f918-105">Szenen im benutzerdefinierten Zusammen-Modus in Microsoft Teams bieten eine immersive und ansprechende Besprechungsumgebung, die Menschen zusammenführt und sie dazu auffordert, ihr Video zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="1f918-105">Custom Together Mode scenes in Microsoft Teams provides an immersive and engaging meeting environment that brings people together and encourages them to turn on their video.</span></span> <span data-ttu-id="1f918-106">Sie kombiniert Teilnehmer digital in einer einzelnen virtuellen Szene und platziert ihre Videostreams in vordefinierten Arbeitsplätzen, die vom Szenenersteller entworfen und behoben wurden.</span><span class="sxs-lookup"><span data-stu-id="1f918-106">It digitally combines participants into a single virtual scene and places their video streams in pre-determined seats designed and fixed by the scene creator.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

<span data-ttu-id="1f918-107">Eine Szene in benutzerdefinierten Szenen im Gemeinsamen Modus ist ein Artefakt, das vom Szenenentwickler mithilfe des Microsoft Scene Studio erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="1f918-107">A scene in custom Together Mode scenes is an artifact created by the scene developer using the Microsoft Scene studio.</span></span> <span data-ttu-id="1f918-108">In einer eingestellten Szeneneinstellung haben die Teilnehmer Arbeitsplätze mit Videostreams festgelegt, die auf diesen Arbeitsplätzen gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-108">In a conceived scene setting, participants have designated seats with video streams rendered in those seats.</span></span>

> [!NOTE]
> <span data-ttu-id="1f918-109">Apps nur für Szenen werden empfohlen, da die Kauferfahrung für solche Apps nahtloser ist.</span><span class="sxs-lookup"><span data-stu-id="1f918-109">Scene only apps are recommended as the acquisition experience for such apps is more seamless.</span></span>

<span data-ttu-id="1f918-110">Der folgende Prozess bietet eine Übersicht zum Erstellen einer Nur-Szene-App:</span><span class="sxs-lookup"><span data-stu-id="1f918-110">The following process gives an overview to create a scene only app:</span></span>

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Nur-Szene-App erstellen" border="false":::

> [!NOTE]
> * <span data-ttu-id="1f918-112">Eine Nur-Szene-App ist immer noch eine App in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1f918-112">A scene only app is still an app in Microsoft Teams.</span></span> <span data-ttu-id="1f918-113">Das Szenenstudio verarbeitet die Erstellung des App-Pakets im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="1f918-113">The Scene studio handles the app package creation in the background.</span></span>
> * <span data-ttu-id="1f918-114">Mehrere Szenen in einem einzelnen App-Paket werden Benutzern als flache Liste von Szenen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f918-114">Multiple scenes in a single app package appear as a flat list of scenes to users.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f918-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1f918-115">Prerequisites</span></span>

<span data-ttu-id="1f918-116">Sie müssen über grundlegende Kenntnisse der folgenden Punkte verfügen, um benutzerdefinierte Szenen im Zusammen-Modus verwenden zu können:</span><span class="sxs-lookup"><span data-stu-id="1f918-116">You must have a basic understanding of the following to use custom Together Mode scenes:</span></span>

* <span data-ttu-id="1f918-117">Definition der Szene und der Arbeitsplätze in einer Szene.</span><span class="sxs-lookup"><span data-stu-id="1f918-117">Definition of scene and seats in a scene.</span></span>
* <span data-ttu-id="1f918-118">Besitzen Sie ein Microsoft Developer-Konto, und machen Sie sich mit dem Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) und App Studio vertraut.</span><span class="sxs-lookup"><span data-stu-id="1f918-118">Have a Microsoft Developer account and be familiar with the Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) and App Studio.</span></span>
* <span data-ttu-id="1f918-119">[Konzept des Querladens von Apps.](../concepts/deploy-and-publish/apps-upload.md)</span><span class="sxs-lookup"><span data-stu-id="1f918-119">[Concept of app sideloading](../concepts/deploy-and-publish/apps-upload.md).</span></span>
* <span data-ttu-id="1f918-120">Stellen Sie sicher, dass der Administrator die Berechtigung zum [**Hochladen einer benutzerdefinierten App**](../concepts/deploy-and-publish/apps-upload.md) und zum Auswählen aller Filter im Rahmen der App-Setup- bzw. Besprechungsrichtlinien erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="1f918-120">Ensure that the Administrator has granted permission to [**Upload a custom app**](../concepts/deploy-and-publish/apps-upload.md) and to select all filters as part of App Setup and Meeting policies respectively.</span></span>

## <a name="best-practices"></a><span data-ttu-id="1f918-121">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="1f918-121">Best practices</span></span>

<span data-ttu-id="1f918-122">Berücksichtigen Sie vor dem Erstellen einer Szene Folgendes, um eine nahtlose Szenenerstellung zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="1f918-122">Prior to building a scene, consider the following to have a seamless scene building experience:</span></span>

* <span data-ttu-id="1f918-123">Stellen Sie sicher, dass alle Bilder im PNG-Format vorliegen.</span><span class="sxs-lookup"><span data-stu-id="1f918-123">Ensure that all images are in PNG format.</span></span>
* <span data-ttu-id="1f918-124">Stellen Sie sicher, dass das endgültige Paket mit allen zusammen zusammengestellten Bildern die Auflösung von 1920 x 1080 nicht überschreiten darf.</span><span class="sxs-lookup"><span data-stu-id="1f918-124">Ensure that the final package with all the images put together must not exceed 1920x1080 resolution.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f918-125">Die Auflösung ist eine gerade Zahl.</span><span class="sxs-lookup"><span data-stu-id="1f918-125">The resolution is an even number.</span></span> <span data-ttu-id="1f918-126">Dies ist eine Voraussetzung dafür, dass Szenen erfolgreich beleuchtet werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-126">This is a requirement for scenes to be lit up successfully.</span></span>

* <span data-ttu-id="1f918-127">Stellen Sie sicher, dass die maximale Szenengröße 10 MB beträgt.</span><span class="sxs-lookup"><span data-stu-id="1f918-127">Ensure that the maximum scene size is 10 MB.</span></span>
* <span data-ttu-id="1f918-128">Stellen Sie sicher, dass die maximale Größe jedes Bilds 5 MB beträgt.</span><span class="sxs-lookup"><span data-stu-id="1f918-128">Ensure that the maximum size of each image is 5 MB.</span></span>

    > [!NOTE]
    > * <span data-ttu-id="1f918-129">Eine Szene ist eine Sammlung mehrerer Bilder.</span><span class="sxs-lookup"><span data-stu-id="1f918-129">A scene is a collection of multiple images.</span></span> <span data-ttu-id="1f918-130">Der Grenzwert gilt für jedes einzelne Bild.</span><span class="sxs-lookup"><span data-stu-id="1f918-130">The limit is for each individual image.</span></span>
    > * <span data-ttu-id="1f918-131">Die individuelle Bildauflösung muss auch eine gerade Zahl sein.</span><span class="sxs-lookup"><span data-stu-id="1f918-131">The individual image resolution must also be an even number.</span></span>
  
* <span data-ttu-id="1f918-132">Stellen Sie sicher, dass das **Kontrollkästchen Transparent** aktiviert ist, wenn das Bild transparent ist.</span><span class="sxs-lookup"><span data-stu-id="1f918-132">Ensure that the **Transparent** checkbox is selected if the image is transparent.</span></span> <span data-ttu-id="1f918-133">Dieses Kontrollkästchen ist im rechten Bereich verfügbar, wenn ein Bild ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="1f918-133">This checkbox is available on the right panel when an image is selected.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f918-134">Überlappende Bilder müssen als **transparent** markiert werden, um anzuzeigen, dass es sich um überlappende Bilder in der Szene handelt.</span><span class="sxs-lookup"><span data-stu-id="1f918-134">Overlapping images need to be marked as **Transparent** to indicate that they are overlapping images in the scene.</span></span>

## <a name="build-a-scene-using-the-scene-studio"></a><span data-ttu-id="1f918-135">Erstellen einer Szene mithilfe des Szenenstudios</span><span class="sxs-lookup"><span data-stu-id="1f918-135">Build a scene using the Scene studio</span></span>

<span data-ttu-id="1f918-136">Microsoft verfügt über ein Szenenstudio, mit dem Sie Szenen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="1f918-136">Microsoft has a Scene studio that allows you to build scenes.</span></span> <span data-ttu-id="1f918-137">Es ist im [Szenen-Editor](https://dev.teams.microsoft.com/scenes)– Teams Entwicklerportal verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1f918-137">It is available on [Scenes Editor - Teams Developer Portal](https://dev.teams.microsoft.com/scenes).</span></span>

> [!NOTE]
> <span data-ttu-id="1f918-138">Dieses Dokument bezieht sich auf Scene Studio im Microsoft Teams Entwicklerportal.</span><span class="sxs-lookup"><span data-stu-id="1f918-138">This document is referring to Scene studio in the Microsoft Teams Developer Portal.</span></span> <span data-ttu-id="1f918-139">Die Benutzeroberfläche und Funktionen sind im App Studio Scene Designer identisch.</span><span class="sxs-lookup"><span data-stu-id="1f918-139">The interface and functionalities are all the same in App Studio Scene Designer.</span></span>

<span data-ttu-id="1f918-140">Eine Szene im Kontext des Szenenstudios ist ein Artefakt, das Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="1f918-140">A scene in the context of the Scene studio is an artifact that contains the following:</span></span>

* <span data-ttu-id="1f918-141">Reservierte Arbeitsplätze für Besprechungsorganisatoren und Besprechungsreferenten.</span><span class="sxs-lookup"><span data-stu-id="1f918-141">Seats reserved for meeting organizer and meeting presenters.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f918-142">Der Referent bezieht sich nicht auf den Benutzer, der aktiv teilt.</span><span class="sxs-lookup"><span data-stu-id="1f918-142">Presenter does not refer to the user who is actively sharing.</span></span> <span data-ttu-id="1f918-143">Es bezieht sich auf die [Besprechungsrolle.](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="1f918-143">It refers to the [meeting role](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

* <span data-ttu-id="1f918-144">Platz und Bild für jeden Teilnehmer mit einer anpassbaren Breite und Höhe.</span><span class="sxs-lookup"><span data-stu-id="1f918-144">Seat and image for each participant with an adjustable width and height.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f918-145">PNG ist das einzige unterstützte Format.</span><span class="sxs-lookup"><span data-stu-id="1f918-145">PNG is the only supported format.</span></span>

* <span data-ttu-id="1f918-146">XYZ-Koordinaten aller Arbeitsplätze und Bilder.</span><span class="sxs-lookup"><span data-stu-id="1f918-146">XYZ coordinates of all the seats and images.</span></span>
* <span data-ttu-id="1f918-147">Sammlung von Bildern, die als ein einziges Bild getarnt sind.</span><span class="sxs-lookup"><span data-stu-id="1f918-147">Collection of images that are camouflaged as one image.</span></span>

<span data-ttu-id="1f918-148">Die Platzabmessungen werden zum Zeichenbereich für das Rendern des Videostreams des Teilnehmers.</span><span class="sxs-lookup"><span data-stu-id="1f918-148">The seat dimensions become the canvas for rendering the participant video stream.</span></span> <span data-ttu-id="1f918-149">Die folgende Abbildung zeigt jeden Platz, der als Avatar zum Erstellen von Szenen dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="1f918-149">The following image shows each seat represented as an avatar for building scenes:</span></span>

![Szenenstudio](../assets/images/apps-in-meetings/scene-design-studio.png)

<span data-ttu-id="1f918-151">**So erstellen Sie eine Szene mit dem Scene Studio**</span><span class="sxs-lookup"><span data-stu-id="1f918-151">**To build a scene using the Scene studio**</span></span>

1. <span data-ttu-id="1f918-152">Wechseln Sie zum [Szenen-Editor – Teams Entwicklerportal.](https://dev.teams.microsoft.com/scenes)</span><span class="sxs-lookup"><span data-stu-id="1f918-152">Go to [Scenes Editor - Teams Developer Portal](https://dev.teams.microsoft.com/scenes).</span></span>

    >[!NOTE]
    > * <span data-ttu-id="1f918-153">Um Scene Studio zu öffnen, können Sie zur Startseite von [Teams Entwicklerportal](https://dev.teams.microsoft.com/home) navigieren und **benutzerdefinierte Szenen für Besprechungen** erstellen auswählen.</span><span class="sxs-lookup"><span data-stu-id="1f918-153">To open Scene studio, you can navigate to the home page of [Teams Developer Portal](https://dev.teams.microsoft.com/home) and select **Create custom scenes for meetings**.</span></span>
    > * <span data-ttu-id="1f918-154">Um Scene Studio zu öffnen, können Sie zur Startseite von [Teams Entwicklerportal](https://dev.teams.microsoft.com/home)navigieren, im linken Abschnitt die Option **"Extras"** und im Abschnitt **"Extras"** das **Szenenstudio** auswählen.</span><span class="sxs-lookup"><span data-stu-id="1f918-154">To open Scene studio, you can navigate to the home page of [Teams Developer Portal](https://dev.teams.microsoft.com/home), select **Tools** from the left hand section, and select **Scene studio** from the **Tools** section.</span></span>

1. <span data-ttu-id="1f918-155">Wählen Sie auf der Seite **"Szenen-Editor"** die Option **"Neue Szene erstellen" aus.**</span><span class="sxs-lookup"><span data-stu-id="1f918-155">In the **Scenes Editor** page, select **Create a new scene**.</span></span>

1. <span data-ttu-id="1f918-156">Geben Sie im **Szenenfeld** einen Namen für die Szene ein.</span><span class="sxs-lookup"><span data-stu-id="1f918-156">In the **Scene** box, enter a name for the scene.</span></span>

    >[!NOTE]
    > * <span data-ttu-id="1f918-157">Sie können **"Schließen"** auswählen, um zwischen dem Schließen oder erneuten Öffnen des rechten Bereichs zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="1f918-157">You can select **Close** to toggle between closing or reopening the right pane.</span></span>
    > * <span data-ttu-id="1f918-158">Sie können die Szene mithilfe der Zoomleiste vergrößern oder verkleinern, um eine bessere Ansicht der Szene zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="1f918-158">You can zoom in or zoom out of the scene using the zoom bar for a better view of the scene.</span></span>

1. <span data-ttu-id="1f918-159">Ziehen Sie das Bild in die Umgebung, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="1f918-159">Drag and drop the image into the environment as displayed in the following image:</span></span>

    >[!NOTE]
    > * <span data-ttu-id="1f918-160">Sie können die [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) herunterladen und Dateien mit den Bildern [SampleApp.zip.](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip)</span><span class="sxs-lookup"><span data-stu-id="1f918-160">You can download the [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) and [SampleApp.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip) files with the images.</span></span>
    > * <span data-ttu-id="1f918-161">Alternativ können Sie der Szene Hintergrundbilder hinzufügen, indem **Sie Bilder hinzufügen.**</span><span class="sxs-lookup"><span data-stu-id="1f918-161">Alternately, you can add background images to the scene using **Add images**.</span></span>

    ![Ziehen in die Szene](../assets/images/apps-in-meetings/drag-and-drop-scene.png)

1. <span data-ttu-id="1f918-163">Wählen Sie das Bild aus, das Sie platziert haben.</span><span class="sxs-lookup"><span data-stu-id="1f918-163">Select the image that you have placed.</span></span>

1. <span data-ttu-id="1f918-164">Wählen Sie im rechten Bereich eine Ausrichtung für das Bild aus, oder verwenden Sie den Schieberegler **"Größe anpassen",** um die Bildgröße anzupassen.</span><span class="sxs-lookup"><span data-stu-id="1f918-164">From the right pane, select an alignment for the image or use the **Resize** slider to adjust the image size.</span></span>

    ![Ausrichtung für Bilder](../assets/images/apps-in-meetings/image-alignment.png)

1. <span data-ttu-id="1f918-166">Wählen Sie einen Bereich außerhalb des Bilds aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-166">Select an area outside of the image.</span></span>

1. <span data-ttu-id="1f918-167">Wählen Sie in der oberen rechten Ecke unter **"Layer"** die Option **"Teilnehmer"** aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-167">In the upper-right corner, select **Participants** under **Layers**.</span></span>

1. <span data-ttu-id="1f918-168">Wählen Sie im Feld "Anzahl der **Teilnehmer"** die Anzahl der Teilnehmer für die Szene aus, und wählen Sie **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-168">Select the number of participants for the scene from the **Number of participants** box, and select **Add**.</span></span>

    >[!NOTE]
    > * <span data-ttu-id="1f918-169">Nachdem die Szene ausgeliefert wurde, werden die Avatar-Platzierungen durch die Videostreams des tatsächlichen Teilnehmers ersetzt.</span><span class="sxs-lookup"><span data-stu-id="1f918-169">After the scene is shipped, the avatar placements are replaced with actual participant's video streams.</span></span>
    > * <span data-ttu-id="1f918-170">Sie können die Teilnehmerbilder um die Szene ziehen und an der erforderlichen Position platzieren und die Größe mithilfe des Größenänderungspfeils ändern.</span><span class="sxs-lookup"><span data-stu-id="1f918-170">You can drag the participant images around the scene and place them in the required position and resize them using the resize arrow.</span></span>

1. <span data-ttu-id="1f918-171">Wählen Sie ein beliebiges Teilnehmerbild aus, und aktivieren Sie das Kontrollkästchen **"Spot zuweisen",** um dem Teilnehmer die Stelle zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="1f918-171">Select any participant image, and select the **Assign Spot** check box to assign the spot to the participant.</span></span>

1. <span data-ttu-id="1f918-172">Wählen Sie die Rolle **"Besprechungsorganisator"** oder **"Referent"** für den Teilnehmer aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-172">Select **Meeting Organizer** or **Presenter** role for the participant.</span></span>

    >[!NOTE]
    > <span data-ttu-id="1f918-173">In einer Besprechung muss einem Teilnehmer die Rolle eines Besprechungsorganisators zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-173">In a meeting, one participant must be assigned the role of a meeting organizer.</span></span>

    ![Spot zuweisen](../assets/images/apps-in-meetings/assign-spot.png)

1. <span data-ttu-id="1f918-175">Wählen Sie **"Speichern"** und **dann "Ansicht" in Teams** aus, um Ihre Szene in Microsoft Teams schnell zu testen.</span><span class="sxs-lookup"><span data-stu-id="1f918-175">Select **Save** and select **View in Teams** to quickly test your scene in Microsoft Teams.</span></span>

    >[!NOTE]
    > * <span data-ttu-id="1f918-176">Wenn Sie **"Ansicht" in Teams** auswählen, wird automatisch eine Microsoft Teams App erstellt, die auf der Seite **"Apps"** im Teams Entwicklerportal angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1f918-176">Selecting **View in Teams** automatically creates a Microsoft Teams app that can be viewed in the **Apps** page in the Teams Developer Portal.</span></span>
    > * <span data-ttu-id="1f918-177">Wenn Sie **"Ansicht" in Teams** auswählen, wird automatisch ein App-Paket erstellt, das hinter der Szene appmanifest.jswird.</span><span class="sxs-lookup"><span data-stu-id="1f918-177">Selecting **View in Teams** automatically creates an app package that is appmanifest.json behind the scene.</span></span> <span data-ttu-id="1f918-178">Wie bereits erwähnt, ist dies abstrahiert, Aber Sie können über das Menü zu **Apps** navigieren, um auf das automatisch erstellte App-Paket zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="1f918-178">As stated earlier, this is abstracted, but you can access the automatically created app package by navigating to **Apps** from the menu.</span></span>
    > * <span data-ttu-id="1f918-179">Um eine von Ihnen erstellte Szene zu löschen, wählen Sie die Szene auf der oberen Leiste **löschen** aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-179">To delete a scene you created, select **Delete scene** on the top bar.</span></span>

1. <span data-ttu-id="1f918-180">Wählen Sie im daraufhin angezeigten Dialogfeld **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-180">In the dialog box that appears, select **Add**.</span></span>

    <span data-ttu-id="1f918-181">Sie können die Szene testen oder darauf zugreifen, indem Sie eine Testbesprechung erstellen und benutzerdefinierte Szenen im Gemeinsamen Modus starten.</span><span class="sxs-lookup"><span data-stu-id="1f918-181">The scene can be tested or accessed by creating a test meeting and launching custom Together Mode scenes.</span></span> <span data-ttu-id="1f918-182">Weitere Informationen finden Sie unter [Aktivieren benutzerdefinierter Szenen für den Zusammen-Modus.](#activate-custom-together-mode-scenes)</span><span class="sxs-lookup"><span data-stu-id="1f918-182">For more information, see [activate custom Together Mode scenes](#activate-custom-together-mode-scenes).</span></span>

    ![Starten von Szenen im benutzerdefinierten Modus "Zusammen"](../assets/images/apps-in-meetings/launchtogethermode.png)

    >[!NOTE]
    > * <span data-ttu-id="1f918-184">Die Szene kann in der benutzerdefinierten Szenengalerie für den Zusammen-Modus angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-184">The scene can be viewed in the custom Together Mode scenes gallery.</span></span>

1. <span data-ttu-id="1f918-185">Optional können Sie im Dropdownmenü **"Speichern"** die Option **"Freigeben"** auswählen, um einen freigabefähigen Link zu erstellen, um Ihre Szenen für andere Benutzer einfach zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="1f918-185">Optionally, you can select **Share** from the **Save** drop-down menu to create a shareable link to easily distribute your scenes for others to use.</span></span> <span data-ttu-id="1f918-186">Durch Öffnen dieses Links wird die Szene für den Benutzer installiert, und er kann mit der Verwendung beginnen.</span><span class="sxs-lookup"><span data-stu-id="1f918-186">Opening this link installs the scene for the user and they can start using it.</span></span>

1. <span data-ttu-id="1f918-187">Nach der Vorschau kann die Szene als App an Teams ausgeliefert werden, indem Sie die Schritte für die App-Übermittlung ausführen.</span><span class="sxs-lookup"><span data-stu-id="1f918-187">After preview, the scene can be shipped as an app to Teams by following the steps for app submission.</span></span>

    >[!NOTE]
    > <span data-ttu-id="1f918-188">Dieser Schritt erfordert das App-Paket, das sich vom Szenenpaket unterscheidet, für die Szene, die entworfen wurde.</span><span class="sxs-lookup"><span data-stu-id="1f918-188">This step requires the app package that is different from the scene package, for the scene that was designed.</span></span> <span data-ttu-id="1f918-189">Das automatisch erstellte App-Paket finden Sie im Abschnitt **"Apps"** im Teams Developer Center.</span><span class="sxs-lookup"><span data-stu-id="1f918-189">The app package created automatically can be found in the **Apps** section in the Teams Developer Center.</span></span>

1. <span data-ttu-id="1f918-190">Optional kann das Szenenpaket abgerufen werden, indem Sie im Dropdownmenü **"Speichern"** die Option **"Exportieren"** auswählen.</span><span class="sxs-lookup"><span data-stu-id="1f918-190">Optionally, the scene package can be retrieved by selecting **Export** from the **Save** drop-down menu.</span></span> <span data-ttu-id="1f918-191">Eine .zip Datei, bei der es sich um das Szenenpaket handelt, wird heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="1f918-191">A .zip file, that is the scene package, is downloaded.</span></span>

    ![Exportieren einer Szene](../assets/images/apps-in-meetings/build-a-scene.png)

    >[!NOTE]
    > <span data-ttu-id="1f918-193">Das Szenenpaket besteht aus einem scene.jsund den PNG-Ressourcen, die zum Erstellen einer Szene verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-193">Scene package comprises of a scene.json and the PNG assets used to build a scene.</span></span> <span data-ttu-id="1f918-194">Das Szenenpaket kann auf andere Änderungen überprüft werden, wie im Beispiel scene.jsim Abschnitt dieses Dokuments beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1f918-194">The scene package can be reviewed for incorporating other changes as described in the Sample scene.json section of this document.</span></span>

<span data-ttu-id="1f918-195">Eine komplexere Szene, die die Z-Achse nutzt, wird im Beispiel für die ersten Schritte veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1f918-195">A more complex scene that leverages the Z-axis is demonstrated in the step-by-step getting started sample.</span></span>

## <a name="sample-scenejson"></a><span data-ttu-id="1f918-196">Beispiel scene.json</span><span class="sxs-lookup"><span data-stu-id="1f918-196">Sample scene.json</span></span>

<span data-ttu-id="1f918-197">Scene.jszusammen mit den Bildern gibt die genaue Position der Arbeitsplätze an.</span><span class="sxs-lookup"><span data-stu-id="1f918-197">Scene.json along with the images indicate the exact position of the seats.</span></span> <span data-ttu-id="1f918-198">Eine Szene besteht aus Bitmapbildern, Sprites und Rechtecke, in die Teilnehmervideos eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-198">A scene consists of bitmap images, sprites, and rectangles to put participant videos in.</span></span> <span data-ttu-id="1f918-199">Diese Sprites und Teilnehmerfelder werden in einem Weltkoordinatensystem definiert, wobei die X-Achse nach rechts und die Y-Achse nach unten zeigen.</span><span class="sxs-lookup"><span data-stu-id="1f918-199">These sprites and participant boxes are defined in a world coordinate system with the X-axis pointing to the right and the Y-axis pointing downwards.</span></span> <span data-ttu-id="1f918-200">Szenen im benutzerdefinierten Zusammen-Modus unterstützen das Vergrößern der aktuellen Teilnehmer.</span><span class="sxs-lookup"><span data-stu-id="1f918-200">Custom Together Mode scenes supports zooming in on the current participants.</span></span> <span data-ttu-id="1f918-201">Dies ist hilfreich für kleine Besprechungen in einer großen Szene.</span><span class="sxs-lookup"><span data-stu-id="1f918-201">This is helpful for small meetings in a large scene.</span></span> <span data-ttu-id="1f918-202">Ein Sprite ist ein statisches Bitmapbild, das in der Welt positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="1f918-202">A sprite is a static bitmap image positioned in the world.</span></span> <span data-ttu-id="1f918-203">Der Z-Wert des Sprite bestimmt die Position des Sprite.</span><span class="sxs-lookup"><span data-stu-id="1f918-203">The Z value of the sprite determines the position of the sprite.</span></span> <span data-ttu-id="1f918-204">Das Rendern beginnt mit dem Sprite mit dem niedrigsten Z-Wert, daher bedeutet ein höherer Z-Wert, dass es näher an der Kamera ist.</span><span class="sxs-lookup"><span data-stu-id="1f918-204">Rendering starts with the sprite with lowest Z value, so higher Z value means it is closer to the camera.</span></span> <span data-ttu-id="1f918-205">Jeder Teilnehmer verfügt über einen eigenen Videofeed, der so segmentiert ist, dass nur der Vordergrund gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="1f918-205">Each participant has its own video feed, which is segmented so that only the foreground is rendered.</span></span>

<span data-ttu-id="1f918-206">Im Folgenden finden Sie die scene.jsim Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1f918-206">Following is the scene.json sample:</span></span>

```json
{
   "protocolVersion": "1.0",
   "id": "A",
   "autoZoom": true,
   "mirrorParticipants ": true,
   "extent":{
      "left":0.0,
      "top":0.0,
      "width":16.0,
      "height":9.0
   },
   "sprites":[
      {
         "filename":"background.png",
         "cx":8.0,
         "cy":4.5,
         "width":16.0,
         "height":9.0,
         "zOrder":0.0,
   "isAlpha":false
      },
      {
         "filename":"table.png",
         "cx":8.0,
         "cy":7.0,
         "width":12.0,
         "height":4.0,
         "zOrder":3.0,
   "isAlpha":true
      },
      {
         "filename":"row0.png",
         "cx":12.0,
         "cy":15.0,
         "width":8.0,
         "height":4.0,
         "zOrder":2.0,
   "isAlpha":true
      }

   ],
   "participants":[
      {
         "cx":5.0,
         "cy":4.0,
         "width":4.0,
         "height":2.25,
         "zOrder":1.0,
         "seatingOrder":0
      },
      {
         "cx":11.0,
         "cy":4.0,
         "width":4.0,
         "height":2.25,
         "zOrder":1.0,
         "seatingOrder":1
      }
   ]
}
```

<span data-ttu-id="1f918-207">Jede Szene hat eine eindeutige ID und einen eindeutigen Namen.</span><span class="sxs-lookup"><span data-stu-id="1f918-207">Each scene has a unique ID and name.</span></span> <span data-ttu-id="1f918-208">Die Szenen-JSON enthält auch Informationen zu allen Ressourcen, die für die Szene verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-208">The scene JSON also contains information on all the assets used for the scene.</span></span> <span data-ttu-id="1f918-209">Jede Ressource enthält einen Dateinamen, eine Breite, eine Höhe und eine Position auf der X- und Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="1f918-209">Each asset contains a filename, width, height, and position on the X and Y-axis.</span></span> <span data-ttu-id="1f918-210">Entsprechend enthält jeder Arbeitsplatz eine Platz-ID, Breite, Höhe und Position auf der X- und Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="1f918-210">Similarly, each seat contains a seat ID, width, height, and position on the X and Y-axis.</span></span> <span data-ttu-id="1f918-211">Die Reihenfolge der Auslastung wird automatisch generiert und kann je nach Präferenz geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-211">The seating order is generated automatically and can be altered as per preference.</span></span>

> [!NOTE]
> <span data-ttu-id="1f918-212">Die Nummer der Reihenfolge der Benachrichtigung entspricht der Reihenfolge der Personen, die dem Anruf beitreten.</span><span class="sxs-lookup"><span data-stu-id="1f918-212">Seating order number corresponds to the order of people joining the call.</span></span>

<span data-ttu-id="1f918-213">Der ZOrder stellt die Reihenfolge dar, in der Bilder und Arbeitsplätze entlang der Z-Achse platziert werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-213">The zOrder represents the order of placing images and seats along the Z-axis.</span></span> <span data-ttu-id="1f918-214">In vielen Fällen gibt es bei Bedarf ein Gefühl von Tiefe oder Partition.</span><span class="sxs-lookup"><span data-stu-id="1f918-214">In many cases, it gives a sense of depth or partition if required.</span></span> <span data-ttu-id="1f918-215">Weitere Informationen finden Sie im Schritt-für-Schritt-Beispiel für die ersten Schritte.</span><span class="sxs-lookup"><span data-stu-id="1f918-215">For more information, see the step-by-step getting started sample.</span></span> <span data-ttu-id="1f918-216">Das Beispiel nutzt zOrder.</span><span class="sxs-lookup"><span data-stu-id="1f918-216">The sample leverages the zOrder.</span></span>

<span data-ttu-id="1f918-217">Nachdem Sie nun das Beispiel scene.jsweiter durchgegangen sind, können Sie die benutzerdefinierten Szenen im Zusammen-Modus aktivieren, um szenenaktiviert zu werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-217">Now that you have gone through the sample scene.json, you can activate the custom Together Mode scenes to engage in scenes.</span></span>

## <a name="activate-custom-together-mode-scenes"></a><span data-ttu-id="1f918-218">Aktivieren von Szenen im benutzerdefinierten Modus "Zusammen"</span><span class="sxs-lookup"><span data-stu-id="1f918-218">Activate custom Together Mode scenes</span></span>

<span data-ttu-id="1f918-219">Hier erhalten Sie End-to-End-Informationen dazu, wie sich ein Endbenutzer mit Szenen in benutzerdefinierten Szenen im Zusammen-Modus beschäftigt.</span><span class="sxs-lookup"><span data-stu-id="1f918-219">Get end-to-end information of how an end user engages with scenes in custom Together Mode scenes.</span></span>

<span data-ttu-id="1f918-220">**So wählen Sie Szenen aus und aktivieren benutzerdefinierte Szenen im Zusammen-Modus**</span><span class="sxs-lookup"><span data-stu-id="1f918-220">**To select scenes and activate custom Together Mode scenes**</span></span>

1. <span data-ttu-id="1f918-221">Erstellen sie eine neue Testbesprechung.</span><span class="sxs-lookup"><span data-stu-id="1f918-221">Create a new test meeting.</span></span>

    >[!NOTE]
    > <span data-ttu-id="1f918-222">Bei Auswahl der **Vorschau** im Szenenstudio wird die Szene als App in Microsoft Teams installiert.</span><span class="sxs-lookup"><span data-stu-id="1f918-222">On selecting **Preview** in the Scene studio, the scene is installed as an app in Microsoft Teams.</span></span> <span data-ttu-id="1f918-223">Dies ist das Modell, mit dem Entwickler Szenen aus dem Szenenstudio testen und ausprobieren können.</span><span class="sxs-lookup"><span data-stu-id="1f918-223">This is the model for a developer to test and try out scenes from the Scene studio.</span></span> <span data-ttu-id="1f918-224">Nachdem eine Szene als App ausgeliefert wurde, sehen Benutzer diese Szenen in der Szenengalerie.</span><span class="sxs-lookup"><span data-stu-id="1f918-224">After a scene is shipped as an app, users see these scenes in the scene gallery.</span></span>

1. <span data-ttu-id="1f918-225">Wählen  Sie in der Dropdownliste Katalog in der oberen linken Ecke den **Modus Zusammen** aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-225">From the **Gallery** drop-down in the upper-left corner, select **Together Mode**.</span></span> <span data-ttu-id="1f918-226">Das Dialogfeld **"Auswahl"** wird angezeigt, und die hinzugefügte Szene ist verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1f918-226">The **Picker** dialog box appears and the scene that is added is available.</span></span>

1. <span data-ttu-id="1f918-227">Wählen Sie **"Szene ändern"** aus, um die Standard-Szene zu ändern.</span><span class="sxs-lookup"><span data-stu-id="1f918-227">Select **Change scene** to change the default scene.</span></span>

1. <span data-ttu-id="1f918-228">Wählen Sie im **Szenenkatalog** die Szene aus, die Sie für Ihre Besprechung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="1f918-228">From the **Scene Gallery**, select the scene you want to use for your meeting.</span></span>

1. <span data-ttu-id="1f918-229">Optional können der Besprechungsorganisator und der Referent die Szene für alle Teilnehmer der Besprechung **ändern.**</span><span class="sxs-lookup"><span data-stu-id="1f918-229">Optionally, the meeting organizer and presenter can **Change scene for all participants** in the meeting.</span></span>

    >[!NOTE]
    > <span data-ttu-id="1f918-230">Zu jedem Zeitpunkt kann nur eine Szene homogen für die Besprechung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-230">At any point in time, only one scene can be used homogeneously for the meeting.</span></span> <span data-ttu-id="1f918-231">Wenn ein Referent oder Organisator eine Szene ändert, wird sie für alle geändert.</span><span class="sxs-lookup"><span data-stu-id="1f918-231">If a presenter or organizer changes a scene, it  changes for all.</span></span> <span data-ttu-id="1f918-232">Das Wechseln in oder aus benutzerdefinierten Szenen für den gemeinsamen Modus ist für einzelne Teilnehmer selbst möglich, aber in benutzerdefinierten Szenen im Gemeinsamen Modus haben alle Teilnehmer dieselbe Szene.</span><span class="sxs-lookup"><span data-stu-id="1f918-232">Switching in or out of custom Together Mode scenes is up to individual participants, but while in custom Together Mode scenes, all participants have the same scene.</span></span>

1. <span data-ttu-id="1f918-233">Wählen Sie **Anwenden** aus.</span><span class="sxs-lookup"><span data-stu-id="1f918-233">Select **Apply**.</span></span> <span data-ttu-id="1f918-234">Teams installiert die App für den Benutzer und wendet die Szene an.</span><span class="sxs-lookup"><span data-stu-id="1f918-234">Teams installs the app for the user and applies the scene.</span></span>

## <a name="open-a-custom-together-mode-scenes-scene-package"></a><span data-ttu-id="1f918-235">Öffnen eines benutzerdefinierten Szenenpakets für den Gemeinsamen Modus</span><span class="sxs-lookup"><span data-stu-id="1f918-235">Open a custom Together Mode scenes Scene Package</span></span>

<span data-ttu-id="1f918-236">Sie können das Szenenpaket, das eine aus dem Szenenstudio abgerufene .zip datei ist, für andere Ersteller freigeben, um die Szene weiter zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="1f918-236">You can share the Scene Package that is a .zip file retrieved from the Scene studio to other creators to further enhance the scene.</span></span> <span data-ttu-id="1f918-237">Die Funktion zum **Importieren einer Szene** kann verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f918-237">The **Import a Scene** functionality can be leveraged.</span></span> <span data-ttu-id="1f918-238">Mit diesem Tool können Sie ein Szenenpaket entpacken, damit der Ersteller die Szene weiter erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="1f918-238">This tool helps unwrap a scene package to let the creator continue building the scene.</span></span>

![Szenen-ZIP-Datei](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a><span data-ttu-id="1f918-240">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1f918-240">See also</span></span>

[<span data-ttu-id="1f918-241">Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="1f918-241">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)
