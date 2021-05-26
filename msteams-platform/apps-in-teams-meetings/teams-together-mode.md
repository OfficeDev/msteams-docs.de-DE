---
title: Together Mode in Teams
description: Arbeiten mit dem Gemeinsamen Modus
ms.topic: conceptual
ms.openlocfilehash: 1620e01ef1825ec43e94614ff8ea355e764e10e0
ms.sourcegitcommit: 1cc1516e71441f6f3f82b35868e21ba9933333cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52651740"
---
# <a name="together-mode-in-teams"></a><span data-ttu-id="e2575-103">Together Mode in Teams</span><span class="sxs-lookup"><span data-stu-id="e2575-103">Together Mode in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="e2575-104">Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e2575-104">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="e2575-105">Microsoft Teams Der Modus "Zusammen" bietet eine immersive und ansprechende Besprechungsumgebung, die Personen zusammen bringt und sie ermutigt, ihr Video zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e2575-105">Microsoft Teams Together Mode provides an immersive and engaging meeting environment that brings people together and encourages them to turn on their video.</span></span> <span data-ttu-id="e2575-106">Es kombiniert Teilnehmer digital zu einer einzelnen virtuellen Szene und platziert ihre Videostreams an vordefinierten, vom Szenenersteller entworfenen und festgelegten Sitzen.</span><span class="sxs-lookup"><span data-stu-id="e2575-106">It digitally combines participants into a single virtual scene and places their video streams in pre-determined seats designed and fixed by the scene creator.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/MGsNmYKgeTA]

<span data-ttu-id="e2575-107">Eine Szene im Gemeinsamen Modus ist ein Artefakt, das vom Szenenentwickler mit dem Microsoft Scene Studio erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="e2575-107">A scene in Together Mode is an artifact created by the scene developer using the Microsoft Scene studio.</span></span> <span data-ttu-id="e2575-108">In einer konzipierten Szeneneinstellung verfügen die Teilnehmer über festgelegte Plätze mit Videostreams, die in diesen Sitzen gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-108">In a conceived scene setting, participants have designated seats with video streams rendered in those seats.</span></span>

> [!NOTE]
> <span data-ttu-id="e2575-109">Nur Szenen-Apps werden empfohlen, da die Kauferfahrung für solche Apps nahtloser ist.</span><span class="sxs-lookup"><span data-stu-id="e2575-109">Scene only apps are recommended as the acquisition experience for such apps is more seamless.</span></span>

<span data-ttu-id="e2575-110">Der folgende Prozess bietet eine Übersicht zum Erstellen einer Nur-Szene-App:</span><span class="sxs-lookup"><span data-stu-id="e2575-110">The following process gives an overview to create a scene only app:</span></span>

:::image type="content" source="../assets/images/apps-in-meetings/create-together-mode-scene-flow.png" alt-text="Nur Szenen-App erstellen" border="false":::

> [!NOTE]
> * <span data-ttu-id="e2575-112">Eine Nur-Szene-App ist immer noch eine App in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e2575-112">A scene only app is still an app in Microsoft Teams.</span></span> <span data-ttu-id="e2575-113">Das Scene Studio verarbeitet die Erstellung von App-Paketen im Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="e2575-113">The Scene studio handles the app package creation in the background.</span></span>
> * <span data-ttu-id="e2575-114">Mehrere Szenen in einem einzelnen App-Paket werden benutzern als flache Liste von Szenen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2575-114">Multiple scenes in a single app package appear as a flat list of scenes to users.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2575-115">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e2575-115">Prerequisites</span></span>

<span data-ttu-id="e2575-116">Sie müssen über grundlegende Kenntnisse der folgenden Funktionen verfügen, um den Gemeinsamen Modus verwenden zu können:</span><span class="sxs-lookup"><span data-stu-id="e2575-116">You must have a basic understanding of the following to use Together Mode:</span></span>

* <span data-ttu-id="e2575-117">Definition von Szene und Sitzen in einer Szene.</span><span class="sxs-lookup"><span data-stu-id="e2575-117">Definition of scene and seats in a scene.</span></span>
* <span data-ttu-id="e2575-118">Verfügen Sie über ein Microsoft Developer-Konto, und machen Sie sich mit Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) und App Studio vertraut.</span><span class="sxs-lookup"><span data-stu-id="e2575-118">Have a Microsoft Developer account and be familiar with the Microsoft Teams [Developer Portal](../concepts/build-and-test/teams-developer-portal.md) and App Studio.</span></span>
* <span data-ttu-id="e2575-119">[Konzept des Querladens von Apps](../concepts/deploy-and-publish/apps-upload.md).</span><span class="sxs-lookup"><span data-stu-id="e2575-119">[Concept of app sideloading](../concepts/deploy-and-publish/apps-upload.md).</span></span>
* <span data-ttu-id="e2575-120">Stellen Sie sicher, dass  der Administrator die Berechtigung zum Hochladen einer benutzerdefinierten App und zum Auswählen aller Filter im Rahmen von App-Setup- bzw. Besprechungsrichtlinien erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="e2575-120">Ensure that the Administrator has granted permission to **Upload a custom app** and to select all filters as part of App Setup and Meeting policies respectively.</span></span>

## <a name="best-practices"></a><span data-ttu-id="e2575-121">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="e2575-121">Best practices</span></span>

<span data-ttu-id="e2575-122">Berücksichtigen Sie vor dem Erstellen einer Szene Folgendes, um eine nahtlose Szenenbildung zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="e2575-122">Prior to building a scene, consider the following to have a seamless scene building experience:</span></span>

* <span data-ttu-id="e2575-123">Stellen Sie sicher, dass alle Bilder im PNG-Format vorliegen.</span><span class="sxs-lookup"><span data-stu-id="e2575-123">Ensure that all images are in PNG format.</span></span>
* <span data-ttu-id="e2575-124">Stellen Sie sicher, dass das endgültige Paket mit allen zusammen 1920 x 1080 Bildern nicht die Auflösung von 1920 x 1080 überschreiten darf.</span><span class="sxs-lookup"><span data-stu-id="e2575-124">Ensure that the final package with all the images put together must not exceed 1920x1080 resolution.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2575-125">Die Auflösung ist eine gleichmäßige Zahl.</span><span class="sxs-lookup"><span data-stu-id="e2575-125">The resolution is an even number.</span></span> <span data-ttu-id="e2575-126">Dies ist eine Voraussetzung dafür, dass Szenen erfolgreich beleuchtet werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-126">This is a requirement for scenes to be lit up successfully.</span></span>

* <span data-ttu-id="e2575-127">Stellen Sie sicher, dass die maximale Szenengröße 10 MB beträgt.</span><span class="sxs-lookup"><span data-stu-id="e2575-127">Ensure that the maximum scene size is 10 MB.</span></span>
* <span data-ttu-id="e2575-128">Stellen Sie sicher, dass die maximale Größe jedes Bilds 5 MB beträgt.</span><span class="sxs-lookup"><span data-stu-id="e2575-128">Ensure that the maximum size of each image is 5 MB.</span></span>

    > [!NOTE]
    > * <span data-ttu-id="e2575-129">Eine Szene ist eine Sammlung mehrerer Bilder.</span><span class="sxs-lookup"><span data-stu-id="e2575-129">A scene is a collection of multiple images.</span></span> <span data-ttu-id="e2575-130">Der Grenzwert gilt für jedes einzelne Bild.</span><span class="sxs-lookup"><span data-stu-id="e2575-130">The limit is for each individual image.</span></span>
    > * <span data-ttu-id="e2575-131">Die einzelne Bildauflösung muss auch eine gleichmäßige Zahl sein.</span><span class="sxs-lookup"><span data-stu-id="e2575-131">The individual image resolution must also be an even number.</span></span>
  
* <span data-ttu-id="e2575-132">Stellen Sie sicher, dass **das Kontrollkästchen Transparent** aktiviert ist, wenn das Bild transparent ist.</span><span class="sxs-lookup"><span data-stu-id="e2575-132">Ensure that the **Transparent** checkbox is selected if the image is transparent.</span></span> <span data-ttu-id="e2575-133">Dieses Kontrollkästchen ist im rechten Bereich verfügbar, wenn ein Bild ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="e2575-133">This checkbox is available on the right panel when an image is selected.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2575-134">Überlappende Bilder müssen als **Transparent gekennzeichnet** werden, um anzuzeigen, dass es sich um überlappende Bilder in der Szene handelt.</span><span class="sxs-lookup"><span data-stu-id="e2575-134">Overlapping images need to be marked as **Transparent** to indicate that they are overlapping images in the scene.</span></span>

## <a name="build-a-scene-using-the-scene-studio"></a><span data-ttu-id="e2575-135">Erstellen einer Szene mithilfe des Szenenstudios</span><span class="sxs-lookup"><span data-stu-id="e2575-135">Build a scene using the Scene studio</span></span>

<span data-ttu-id="e2575-136">Microsoft verfügt über ein Szenenstudio, mit dem Sie Szenen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="e2575-136">Microsoft has a Scene studio that allows you to build scenes.</span></span> <span data-ttu-id="e2575-137">Sie ist im [Szenen-Editor verfügbar– Teams Entwicklerportal](https://dev.teams.microsoft.com/scenes).</span><span class="sxs-lookup"><span data-stu-id="e2575-137">It is available on [Scenes Editor - Teams Developer Portal](https://dev.teams.microsoft.com/scenes).</span></span>

> [!NOTE]
> <span data-ttu-id="e2575-138">Dieses Dokument bezieht sich auf Scene studio im Microsoft Teams Developer Portal.</span><span class="sxs-lookup"><span data-stu-id="e2575-138">This document is referring to Scene studio in the Microsoft Teams Developer Portal.</span></span> <span data-ttu-id="e2575-139">Die Benutzeroberfläche und die Funktionen sind im App Studio Scene Designer identisch.</span><span class="sxs-lookup"><span data-stu-id="e2575-139">The interface and functionalities are all the same in App Studio Scene Designer.</span></span>

<span data-ttu-id="e2575-140">Eine Szene im Kontext des Szenenstudios ist ein Artefakt, das Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="e2575-140">A scene in the context of the Scene studio is an artifact that contains the following:</span></span>

* <span data-ttu-id="e2575-141">Reservierte Plätze für Besprechungsorganisatoren und Besprechungsorganisatoren.</span><span class="sxs-lookup"><span data-stu-id="e2575-141">Seats reserved for meeting organizer and meeting presenters.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2575-142">Der Presenter bezieht sich nicht auf den Benutzer, der aktiv freigaben möchte.</span><span class="sxs-lookup"><span data-stu-id="e2575-142">Presenter does not refer to the user who is actively sharing.</span></span> <span data-ttu-id="e2575-143">Er bezieht sich auf die [Besprechungsrolle](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="e2575-143">It refers to the [meeting role](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

* <span data-ttu-id="e2575-144">Platz und Bild für jeden Teilnehmer mit einer anpassbaren Breite und Höhe.</span><span class="sxs-lookup"><span data-stu-id="e2575-144">Seat and image for each participant with an adjustable width and height.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2575-145">PNG ist das einzige unterstützte Format.</span><span class="sxs-lookup"><span data-stu-id="e2575-145">PNG is the only supported format.</span></span>

* <span data-ttu-id="e2575-146">XYZ-Koordinaten aller Sitze und Bilder.</span><span class="sxs-lookup"><span data-stu-id="e2575-146">XYZ coordinates of all the seats and images.</span></span>
* <span data-ttu-id="e2575-147">Sammlung von Bildern, die als ein Bild getarnt sind.</span><span class="sxs-lookup"><span data-stu-id="e2575-147">Collection of images that are camouflaged as one image.</span></span>

<span data-ttu-id="e2575-148">Die Größe des Platzes wird zum Zeichenbereich für das Rendern des Teilnehmervideostreams.</span><span class="sxs-lookup"><span data-stu-id="e2575-148">The seat dimensions become the canvas for rendering the participant video stream.</span></span> <span data-ttu-id="e2575-149">Die folgende Abbildung zeigt jeden Platz, der als Avatar für das Erstellen von Szenen dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="e2575-149">The following image shows each seat represented as an avatar for building scenes:</span></span>

![Szenenstudio](../assets/images/apps-in-meetings/scene-design-studio.png)

<span data-ttu-id="e2575-151">**So erstellen Sie eine Szene mithilfe des Szenenstudios**</span><span class="sxs-lookup"><span data-stu-id="e2575-151">**To build a scene using the Scene studio**</span></span>

1. <span data-ttu-id="e2575-152">Wechseln Sie [zu Szenen-Editor – Teams Developer Portal](https://dev.teams.microsoft.com/scenes).</span><span class="sxs-lookup"><span data-stu-id="e2575-152">Go to [Scenes Editor - Teams Developer Portal](https://dev.teams.microsoft.com/scenes).</span></span>

    >[!NOTE]
    > * <span data-ttu-id="e2575-153">Zum Öffnen von Scene Studio können Sie zur Startseite des [Teams-Entwicklerportals](https://dev.teams.microsoft.com/home) navigieren und benutzerdefinierte Szenen für **Besprechungen erstellen auswählen.**</span><span class="sxs-lookup"><span data-stu-id="e2575-153">To open Scene studio, you can navigate to the home page of [Teams Developer Portal](https://dev.teams.microsoft.com/home) and select **Create custom scenes for meetings**.</span></span>
    > * <span data-ttu-id="e2575-154">Zum Öffnen von Scene Studio können Sie zur Startseite von [Teams Developer Portal](https://dev.teams.microsoft.com/home)navigieren, im  linken Abschnitt Tools auswählen und im Abschnitt **Extras** szenenstudio auswählen. </span><span class="sxs-lookup"><span data-stu-id="e2575-154">To open Scene studio, you can navigate to the home page of [Teams Developer Portal](https://dev.teams.microsoft.com/home), select **Tools** from the left hand section, and select **Scene studio** from the **Tools** section.</span></span>

1. <span data-ttu-id="e2575-155">Wählen Sie **auf der** Seite Szenen-Editor die Option Neue Szene **erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="e2575-155">In the **Scenes Editor** page, select **Create a new scene**.</span></span>

1. <span data-ttu-id="e2575-156">Geben Sie **im Feld Szene** einen Namen für die Szene ein.</span><span class="sxs-lookup"><span data-stu-id="e2575-156">In the **Scene** box, enter a name for the scene.</span></span>

    >[!NOTE]
    > * <span data-ttu-id="e2575-157">Sie können Schließen **auswählen,** um zwischen dem Schließen oder erneuten Öffnen des rechten Bereichs umschalten zu können.</span><span class="sxs-lookup"><span data-stu-id="e2575-157">You can select **Close** to toggle between closing or reopening the right pane.</span></span>
    > * <span data-ttu-id="e2575-158">Sie können die Szene mithilfe der Zoomleiste vergrößern oder verkleinern, um eine bessere Ansicht der Szene zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e2575-158">You can zoom in or zoom out of the scene using the zoom bar for a better view of the scene.</span></span>

1. <span data-ttu-id="e2575-159">Ziehen Sie das Bild in die Umgebung, wie in der folgenden Abbildung dargestellt, und legen Sie es in die Umgebung ab:</span><span class="sxs-lookup"><span data-stu-id="e2575-159">Drag and drop the image into the environment as displayed in the following image:</span></span>

    >[!NOTE]
    > * <span data-ttu-id="e2575-160">Sie können die dateien [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) [ undSampleApp.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip) mit den Bildern herunterladen.</span><span class="sxs-lookup"><span data-stu-id="e2575-160">You can download the [SampleScene.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleScene.zip) and [SampleApp.zip](https://github.com/MicrosoftDocs/msteams-docs/tree/master/msteams-platform/apps-in-teams-meetings/SampleApp.zip) files with the images.</span></span>
    > * <span data-ttu-id="e2575-161">Alternativ können Sie der Szene Hintergrundbilder hinzufügen, indem **Sie Bilder hinzufügen verwenden.**</span><span class="sxs-lookup"><span data-stu-id="e2575-161">Alternately, you can add background images to the scene using **Add images**.</span></span>

    ![Ziehen in die Szene](../assets/images/apps-in-meetings/drag-and-drop-scene.png)

1. <span data-ttu-id="e2575-163">Wählen Sie das Bild aus, das Sie platziert haben.</span><span class="sxs-lookup"><span data-stu-id="e2575-163">Select the image that you have placed.</span></span>

1. <span data-ttu-id="e2575-164">Wählen Sie im rechten Bereich eine Ausrichtung für das Bild aus, oder verwenden Sie **den** Schieberegler Größenänderung, um die Bildgröße anzupassen.</span><span class="sxs-lookup"><span data-stu-id="e2575-164">From the right pane, select an alignment for the image or use the **Resize** slider to adjust the image size.</span></span>

    ![Ausrichtung für Bilder](../assets/images/apps-in-meetings/image-alignment.png)

1. <span data-ttu-id="e2575-166">Wählen Sie einen Bereich außerhalb des Bilds aus.</span><span class="sxs-lookup"><span data-stu-id="e2575-166">Select an area outside of the image.</span></span>

1. <span data-ttu-id="e2575-167">Wählen Sie in der oberen rechten Ecke unter **Ebenen die** Option **Teilnehmer aus.**</span><span class="sxs-lookup"><span data-stu-id="e2575-167">In the upper-right corner, select **Participants** under **Layers**.</span></span>

1. <span data-ttu-id="e2575-168">Wählen Sie im Feld Anzahl  der Teilnehmer die Anzahl der Teilnehmer für die Szene aus, und wählen Sie **Hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="e2575-168">Select the number of participants for the scene from the **Number of participants** box, and select **Add**.</span></span>

    >[!NOTE]
    > * <span data-ttu-id="e2575-169">Nachdem die Szene versendet wurde, werden die Avatarplatzierungen durch die Videostreams des tatsächlichen Teilnehmers ersetzt.</span><span class="sxs-lookup"><span data-stu-id="e2575-169">After the scene is shipped, the avatar placements are replaced with actual participant's video streams.</span></span>
    > * <span data-ttu-id="e2575-170">Sie können die Teilnehmerbilder um die Szene ziehen und sie an der erforderlichen Position platzieren und die Größe mithilfe des Größenänderungspfeils ändern.</span><span class="sxs-lookup"><span data-stu-id="e2575-170">You can drag the participant images around the scene and place them in the required position and resize them using the resize arrow.</span></span>

1. <span data-ttu-id="e2575-171">Wählen Sie ein beliebiges Teilnehmerbild aus, und aktivieren Sie das Kontrollkästchen **Spot** zuweisen, um den Spot dem Teilnehmer zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="e2575-171">Select any participant image, and choose the **Assign Spot** check box to assign the spot to the participant.</span></span>

1. <span data-ttu-id="e2575-172">Wählen **Sie die Rolle** "Besprechungsorganisator" oder **"Organisator"** für den Teilnehmer aus.</span><span class="sxs-lookup"><span data-stu-id="e2575-172">Select **Meeting Organizer** or **Presenter** role for the participant.</span></span>

    >[!NOTE]
    > <span data-ttu-id="e2575-173">In einer Besprechung muss einem Teilnehmer die Rolle eines Besprechungsorganisators zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-173">In a meeting, one participant must be assigned the role of a meeting organizer.</span></span>

    ![Spot zuweisen](../assets/images/apps-in-meetings/assign-spot.png)

1. <span data-ttu-id="e2575-175">Wählen **Sie Speichern** aus, und **wählen** Teams ansicht aus, um Ihre Szene in einem Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e2575-175">Select **Save** and select **View in Teams** to quickly test your scene in Microsoft Teams.</span></span>

    >[!NOTE]
    > <span data-ttu-id="e2575-176">Wenn Sie eine von Ihnen erstellte Szene löschen möchten, wählen **Sie szene löschen in** der oberen Leiste aus.</span><span class="sxs-lookup"><span data-stu-id="e2575-176">To delete a scene you created, select **Delete scene** on the top bar.</span></span>

1. <span data-ttu-id="e2575-177">Wählen Sie im Dialogfeld **Ansicht in Teams** vorschau in **Teams** aus.</span><span class="sxs-lookup"><span data-stu-id="e2575-177">In the **View in Teams** dialog box, select **Preview in Teams**.</span></span>
1. <span data-ttu-id="e2575-178">Wählen Sie im angezeigten Dialogfeld Hinzufügen **aus.**</span><span class="sxs-lookup"><span data-stu-id="e2575-178">In the dialog box that appears, select **Add**.</span></span>

    <span data-ttu-id="e2575-179">Die Szene kann getestet oder zugegriffen werden, indem Sie eine Testsitzung erstellen und den Gemeinsamen Modus starten.</span><span class="sxs-lookup"><span data-stu-id="e2575-179">The scene can be tested or accessed by creating a test meeting and launching Together Mode.</span></span> <span data-ttu-id="e2575-180">Weitere Informationen finden Sie unter [Aktivieren des Gemeinsamen Modus](#activate-the-together-mode).</span><span class="sxs-lookup"><span data-stu-id="e2575-180">For more information, see [activate the Together Mode](#activate-the-together-mode).</span></span>

    ![Gemeinsamen Modus starten](../assets/images/apps-in-meetings/launchtogethermode.png)

    >[!NOTE]
    > * <span data-ttu-id="e2575-182">Durch **Auswählen der** Vorschau wird automatisch Microsoft Teams App erstellt, die auf der Seite **Apps** im Teams angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e2575-182">Selecting **Preview** automatically creates a Microsoft Teams app that can be viewed in the **Apps** page in the Teams Developer Portal.</span></span>
    > * <span data-ttu-id="e2575-183">Durch **Auswählen der Vorschau** wird automatisch ein App-Paket erstellt, appmanifest.jshinter der Szene angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e2575-183">Selecting **Preview** automatically creates an app package that is appmanifest.json behind the scene.</span></span> <span data-ttu-id="e2575-184">Wie bereits erwähnt, ist dies abstrahiert, Sie können jedoch auf das automatisch erstellte App-Paket zugreifen, indem Sie über das Menü zu **Apps** navigieren.</span><span class="sxs-lookup"><span data-stu-id="e2575-184">As stated earlier, this is abstracted, but you can access the automatically created app package by navigating to **Apps** from the menu.</span></span>
    > * <span data-ttu-id="e2575-185">Die Szene kann dann im Szenenkatalog für den gemeinsamen Modus angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-185">The scene can then be viewed in the Together Mode scene gallery.</span></span>

1. <span data-ttu-id="e2575-186">Optional können Sie  im Dropdownmenü Speichern die Option Freigeben auswählen, um einen freigabebaren Link zu erstellen, um Ihre Szenen für andere Benutzer einfach zu verteilen. </span><span class="sxs-lookup"><span data-stu-id="e2575-186">Optionally, you can select **Share** from the **Save** drop-down menu to create a shareable link to easily distribute your scenes for others to use.</span></span> <span data-ttu-id="e2575-187">Wenn Sie diesen Link öffnen, wird die Szene für den Benutzer installiert, und er kann mit der Verwendung beginnen.</span><span class="sxs-lookup"><span data-stu-id="e2575-187">Opening this link installs the scene for the user and they can start using it.</span></span>

1. <span data-ttu-id="e2575-188">Nach der Vorschau kann die Szene als App an Teams, indem Sie die Schritte für die App-Übermittlung ausführen.</span><span class="sxs-lookup"><span data-stu-id="e2575-188">After preview, the scene can be shipped as an app to Teams by following the steps for app submission.</span></span>

    >[!NOTE]
    > <span data-ttu-id="e2575-189">Dieser Schritt erfordert das Vom Szenenpaket unterschiedliche App-Paket für die entworfene Szene.</span><span class="sxs-lookup"><span data-stu-id="e2575-189">This step requires the app package that is different from the scene package, for the scene that was designed.</span></span> <span data-ttu-id="e2575-190">Das automatisch erstellte App-Paket finden Sie im Abschnitt **Apps** im Teams Developer Center.</span><span class="sxs-lookup"><span data-stu-id="e2575-190">The app package created automatically can be found in the **Apps** section in the Teams Developer Center.</span></span>

1. <span data-ttu-id="e2575-191">Optional kann das Szenenpaket abgerufen werden, indem  Sie im Dropdownmenü Speichern auf **Exportieren** klicken.</span><span class="sxs-lookup"><span data-stu-id="e2575-191">Optionally, the scene package can be retrieved by selecting **Export** from the **Save** drop-down menu.</span></span> <span data-ttu-id="e2575-192">Eine .zip, d. h. das Szenenpaket, wird heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="e2575-192">A .zip file, that is the scene package, is downloaded.</span></span>

    ![Exportieren einer Szene](../assets/images/apps-in-meetings/build-a-scene.png)

    >[!NOTE]
    > <span data-ttu-id="e2575-194">Das Szenenpaket besteht aus einem scene.jsund den PNG-Ressourcen, die zum Erstellen einer Szene verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-194">Scene package comprises of a scene.json and the PNG assets used to build a scene.</span></span> <span data-ttu-id="e2575-195">Das Szenenpaket kann für die Einbindung anderer Änderungen überprüft werden, wie im Abschnitt Beispiel scene.jsabschnitt dieses Dokuments beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e2575-195">The scene package can be reviewed for incorporating other changes as described in the Sample scene.json section of this document.</span></span>

<span data-ttu-id="e2575-196">Eine komplexere Szene, die die Z-Achse nutzt, wird im Schrittweisen Beispiel für erste Schritte gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2575-196">A more complex scene that leverages the Z-axis is demonstrated in the step-by-step getting started sample.</span></span>

## <a name="sample-scenejson"></a><span data-ttu-id="e2575-197">Beispiel scene.json</span><span class="sxs-lookup"><span data-stu-id="e2575-197">Sample scene.json</span></span>

<span data-ttu-id="e2575-198">Scene.jszusammen mit den Bildern geben Sie die genaue Position der Sitze an.</span><span class="sxs-lookup"><span data-stu-id="e2575-198">Scene.json along with the images indicate the exact position of the seats.</span></span> <span data-ttu-id="e2575-199">Eine Szene besteht aus Bitmapbildern, Sprites und Rechtecken, in die Teilnehmervideos eingefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="e2575-199">A scene consists of bitmap images, sprites, and rectangles to put participant videos in.</span></span> <span data-ttu-id="e2575-200">Diese Sprites und Teilnehmerfelder werden in einem Weltkoordinatensystem definiert, bei dem die X-Achse nach rechts und die Y-Achse nach unten zeigt.</span><span class="sxs-lookup"><span data-stu-id="e2575-200">These sprites and participant boxes are defined in a world coordinate system with the X-axis pointing to the right and the Y-axis pointing downwards.</span></span> <span data-ttu-id="e2575-201">Der Modus "Zusammen" unterstützt das Vergrößern der aktuellen Teilnehmer.</span><span class="sxs-lookup"><span data-stu-id="e2575-201">Together mode supports zooming in on the current participants.</span></span> <span data-ttu-id="e2575-202">Dies ist für kleine Besprechungen in einer großen Szene hilfreich.</span><span class="sxs-lookup"><span data-stu-id="e2575-202">This is helpful for small meetings in a large scene.</span></span> <span data-ttu-id="e2575-203">Ein sprite ist ein statisches Bitmapbild, das in der Welt positioniert ist.</span><span class="sxs-lookup"><span data-stu-id="e2575-203">A sprite is a static bitmap image positioned in the world.</span></span> <span data-ttu-id="e2575-204">Der Z-Wert des sprite bestimmt die Position des sprite.</span><span class="sxs-lookup"><span data-stu-id="e2575-204">The Z value of the sprite determines the position of the sprite.</span></span> <span data-ttu-id="e2575-205">Das Rendern beginnt mit dem sprite mit dem niedrigsten Z-Wert, sodass ein höherer Z-Wert bedeutet, dass er näher an der Kamera liegt.</span><span class="sxs-lookup"><span data-stu-id="e2575-205">Rendering starts with the sprite with lowest Z value, so higher Z value means it is closer to the camera.</span></span> <span data-ttu-id="e2575-206">Jeder Teilnehmer verfügt über einen eigenen Videofeed, der segmentiert ist, sodass nur der Vordergrund gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="e2575-206">Each participant has its own video feed, which is segmented so that only the foreground is rendered.</span></span>

<span data-ttu-id="e2575-207">Nachfolgend finden Sie scene.jsBeispiel:</span><span class="sxs-lookup"><span data-stu-id="e2575-207">Following is the scene.json sample:</span></span>

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

<span data-ttu-id="e2575-208">Jede Szene hat eine eindeutige ID und einen eindeutigen Namen.</span><span class="sxs-lookup"><span data-stu-id="e2575-208">Each scene has a unique ID and name.</span></span> <span data-ttu-id="e2575-209">Das Szenen-JSON enthält außerdem Informationen zu allen ressourcen, die für die Szene verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-209">The scene JSON also contains information on all the assets used for the scene.</span></span> <span data-ttu-id="e2575-210">Jede Ressource enthält einen Dateinamen, eine Breite, eine Höhe und eine Position auf der X- und Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="e2575-210">Each asset contains a filename, width, height, and position on the X and Y-axis.</span></span> <span data-ttu-id="e2575-211">Entsprechend enthält jeder Sitz eine Sitz-ID, Breite, Höhe und Position auf der X- und Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="e2575-211">Similarly, each seat contains a seat ID, width, height, and position on the X and Y-axis.</span></span> <span data-ttu-id="e2575-212">Die Sitzreihenfolge wird automatisch generiert und kann je nach Einstellung geändert werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-212">The seating order is generated automatically and can be altered as per preference.</span></span>

> [!NOTE]
> <span data-ttu-id="e2575-213">Die Nummer der Sitzreihenfolge entspricht der Reihenfolge der Personen, die dem Anruf beitreten.</span><span class="sxs-lookup"><span data-stu-id="e2575-213">Seating order number corresponds to the order of people joining the call.</span></span>

<span data-ttu-id="e2575-214">Die zOrder stellt die Reihenfolge dar, in der Bilder und Sitze entlang der Z-Achse platziert werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-214">The zOrder represents the order of placing images and seats along the Z-axis.</span></span> <span data-ttu-id="e2575-215">In vielen Fällen gibt es ein Gefühl von Tiefe oder Partition, falls erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e2575-215">In many cases, it gives a sense of depth or partition if required.</span></span> <span data-ttu-id="e2575-216">Weitere Informationen finden Sie im Schrittweisen Beispiel für erste Schritte.</span><span class="sxs-lookup"><span data-stu-id="e2575-216">For more information, see the step-by-step getting started sample.</span></span> <span data-ttu-id="e2575-217">Das Beispiel nutzt die zOrder.</span><span class="sxs-lookup"><span data-stu-id="e2575-217">The sample leverages the zOrder.</span></span>

<span data-ttu-id="e2575-218">Nachdem Sie die Beispielanwendung scene.jshaben, können Sie den Modus "Zusammen" aktivieren, um an Szenen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="e2575-218">Now that you have gone through the sample scene.json, you can activate the Together Mode to engage in scenes.</span></span>

## <a name="activate-the-together-mode"></a><span data-ttu-id="e2575-219">Aktivieren des Gemeinsamen Modus</span><span class="sxs-lookup"><span data-stu-id="e2575-219">Activate the Together Mode</span></span>

<span data-ttu-id="e2575-220">Erhalten Sie End-to-End-Informationen darüber, wie sich ein Endbenutzer mit Szenen im Gemeinsamen Modus beschäftigt.</span><span class="sxs-lookup"><span data-stu-id="e2575-220">Get end-to-end information of how an end user engages with scenes in Together Mode.</span></span>

<span data-ttu-id="e2575-221">**So wählen Sie Szenen aus, und aktivieren Sie den Gemeinsamen Modus**</span><span class="sxs-lookup"><span data-stu-id="e2575-221">**To choose scenes and activate the Together Mode**</span></span>

1. <span data-ttu-id="e2575-222">Erstellen Sie eine neue Testsitzung.</span><span class="sxs-lookup"><span data-stu-id="e2575-222">Create a new test meeting.</span></span>

    >[!NOTE]
    > <span data-ttu-id="e2575-223">Beim Auswählen **der Vorschau** im Szenenstudio wird die Szene als App in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e2575-223">On selecting **Preview** in the Scene studio, the scene is installed as an app in Microsoft Teams.</span></span> <span data-ttu-id="e2575-224">Dies ist das Modell für einen Entwickler, um Szenen aus dem Szenenstudio zu testen und auszuprobieren.</span><span class="sxs-lookup"><span data-stu-id="e2575-224">This is the model for a developer to test and try out scenes from the Scene studio.</span></span> <span data-ttu-id="e2575-225">Nachdem eine Szene als App versendet wurde, werden diese Szenen im Szenenkatalog angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2575-225">After a scene is shipped as an app, users see these scenes in the scene gallery.</span></span>

1. <span data-ttu-id="e2575-226">Wählen Sie **in** der Dropdownliste Galerie in der oberen linken Ecke zusammen **Modus aus.**</span><span class="sxs-lookup"><span data-stu-id="e2575-226">From the **Gallery** drop-down in the upper-left corner, select **Together Mode**.</span></span> <span data-ttu-id="e2575-227">Das **Dialogfeld Auswahl** wird angezeigt, und die hinzugefügte Szene ist verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e2575-227">The **Picker** dialog box appears and the scene that is added is available.</span></span>

1. <span data-ttu-id="e2575-228">Wählen **Sie Szene ändern aus,** um die Standardszene zu ändern.</span><span class="sxs-lookup"><span data-stu-id="e2575-228">Select **Change scene** to change the default scene.</span></span>

1. <span data-ttu-id="e2575-229">Wählen Sie **im Szenenkatalog** die Szene aus, die Sie für Ihre Besprechung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="e2575-229">From the **Scene Gallery**, select the scene you want to use for your meeting.</span></span>

1. <span data-ttu-id="e2575-230">Optional können der Besprechungsorganisator und der Organisator in der Besprechung den Modus **Alle** Teilnehmer in den Gemeinsamen Modus wechseln auswählen.</span><span class="sxs-lookup"><span data-stu-id="e2575-230">Optionally, the meeting organizer and presenter can choose **Switch all participants to together mode** in the meeting.</span></span>

    >[!NOTE]
    > <span data-ttu-id="e2575-231">Zu jedem Beliebigen Zeitpunkt kann nur eine Szene homogen für die Besprechung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-231">At any point in time, only one scene can be used homogeneously for the meeting.</span></span> <span data-ttu-id="e2575-232">Wenn ein Organisator oder ein Organisator eine Szene ändert, ändert sie sich für alle.</span><span class="sxs-lookup"><span data-stu-id="e2575-232">If a presenter or organizer changes a scene, it  changes for all.</span></span> <span data-ttu-id="e2575-233">Das Wechseln in oder aus dem Gemeinsamen Modus liegt bei einzelnen Teilnehmern, aber im Gemeinsamen Modus haben alle Teilnehmer dieselbe Szene.</span><span class="sxs-lookup"><span data-stu-id="e2575-233">Switching in or out of Together Mode is up to individual participants, but while in Together Mode, all participants have the same scene.</span></span>

1. <span data-ttu-id="e2575-234">Wählen Sie **Anwenden** aus.</span><span class="sxs-lookup"><span data-stu-id="e2575-234">Select **Apply**.</span></span> <span data-ttu-id="e2575-235">Teams installiert die App für den Benutzer und wendet die Szene an.</span><span class="sxs-lookup"><span data-stu-id="e2575-235">Teams installs the app for the user and applies the scene.</span></span>

## <a name="open-a-together-mode-scene-package"></a><span data-ttu-id="e2575-236">Öffnen eines Szenenpakets für den gemeinsamen Modus</span><span class="sxs-lookup"><span data-stu-id="e2575-236">Open a Together Mode Scene Package</span></span>

<span data-ttu-id="e2575-237">Sie können das Szenenpaket, bei dem es sich um eine .zip, die aus dem Szenenstudio abgerufen wurde, für andere Ersteller freigeben, um die Szene weiter zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="e2575-237">You can share the Scene Package that is a .zip file retrieved from the Scene studio to other creators to further enhance the scene.</span></span> <span data-ttu-id="e2575-238">Die **Funktion "Szene importieren"** kann genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="e2575-238">The **Import a Scene** functionality can be leveraged.</span></span> <span data-ttu-id="e2575-239">Dieses Tool hilft beim Auspacken eines Szenenpakets, damit der Ersteller die Szene weiter erstellt.</span><span class="sxs-lookup"><span data-stu-id="e2575-239">This tool helps unwrap a scene package to let the creator continue building the scene.</span></span>

![Szenen-ZIP-Datei](../assets/images/apps-in-meetings/scene-zip-file.png)

## <a name="see-also"></a><span data-ttu-id="e2575-241">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e2575-241">See also</span></span>

[<span data-ttu-id="e2575-242">Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="e2575-242">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)
