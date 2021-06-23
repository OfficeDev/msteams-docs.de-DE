---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
author: surbhigupta
description: Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen
ms.topic: conceptual
ms.openlocfilehash: e31e241a61f40a8dc2b8a1221765bd4755d346ed
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068644"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a><span data-ttu-id="14b27-103">Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="14b27-103">Enable and configure your apps for Teams meetings</span></span>

<span data-ttu-id="14b27-104">Jedes Team hat eine andere Art, Aufgaben zu kommunizieren und zusammenzuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="14b27-104">Every team has a different way of communicating and collaborating tasks.</span></span> <span data-ttu-id="14b27-105">Sie können diese verschiedenen Aufgaben erreichen, indem Sie Teams mit Apps für Besprechungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="14b27-105">You can achieve these different tasks by customizing Teams with apps for meetings.</span></span> <span data-ttu-id="14b27-106">Um unterschiedliche Aufgaben anzupassen und zu erreichen, müssen Sie Ihre Apps für Teams Besprechungen aktivieren und Ihre Apps so konfigurieren, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="14b27-106">To customize and to achieve different tasks, you must enable your apps for Teams meetings and configure your apps to be available in meeting scope within their app manifest.</span></span>

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="14b27-107">Aktivieren Ihrer App für Teams Besprechungen</span><span class="sxs-lookup"><span data-stu-id="14b27-107">Enable your app for Teams meetings</span></span>

<span data-ttu-id="14b27-108">Um Ihre App für Teams Besprechungen zu aktivieren, müssen Sie Ihr App-Manifest aktualisieren und anhand der Kontexteigenschaften bestimmen, wo Ihre App angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="14b27-108">To enable your app for Teams meetings, you must update your app manifest and use the context properties to determine where your app must appear.</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="14b27-109">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="14b27-109">Update your app manifest</span></span>

<span data-ttu-id="14b27-110">Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe von `configurableTabs` `scopes` , und `context` Arrays deklariert.</span><span class="sxs-lookup"><span data-stu-id="14b27-110">The meetings app capabilities are declared in your app manifest using the `configurableTabs`, `scopes`, and `context` arrays.</span></span> <span data-ttu-id="14b27-111">Der Bereich definiert, für wen und welcher Kontext definiert, wo Ihre App verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="14b27-111">Scope defines to whom and context defines where your app is available.</span></span>

> [!NOTE]
> * <span data-ttu-id="14b27-112">Versuchen Sie, Das App-Manifest mit dem [Manifestschema](../resources/schema/manifest-schema-dev-preview.md)zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="14b27-112">Try updating your app manifest with the [manifest schema](../resources/schema/manifest-schema-dev-preview.md).</span></span>
> * <span data-ttu-id="14b27-113">Apps in Besprechungen erfordern den Gruppenchatbereich.</span><span class="sxs-lookup"><span data-stu-id="14b27-113">Apps in meetings require groupchat scope.</span></span> <span data-ttu-id="14b27-114">Der Teambereich funktioniert nur für Registerkarten in Kanälen.</span><span class="sxs-lookup"><span data-stu-id="14b27-114">The team scope works for tabs in channels only.</span></span>

<span data-ttu-id="14b27-115">Das App-Manifest muss den folgenden Codeausschnitt enthalten:</span><span class="sxs-lookup"><span data-stu-id="14b27-115">The app manifest must include the following code snippet:</span></span>

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team",
        "groupchat"
      ],
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

> [!NOTE]
> <span data-ttu-id="14b27-116">`meetingStage` ist derzeit nur in der [Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="14b27-116">`meetingStage` is currently available in [developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

### <a name="context-property"></a><span data-ttu-id="14b27-117">Context-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="14b27-117">Context property</span></span>

<span data-ttu-id="14b27-118">Die `context` Eigenschaft bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo der Benutzer die App aufruft.</span><span class="sxs-lookup"><span data-stu-id="14b27-118">The `context` property determines what must be shown when a user invokes an app in a meeting depending on where the user invokes the app.</span></span> <span data-ttu-id="14b27-119">Mit der Registerkarte `context` und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss.</span><span class="sxs-lookup"><span data-stu-id="14b27-119">The tab `context` and `scopes` properties enable you to determine where your app must appear.</span></span> <span data-ttu-id="14b27-120">Registerkarten im `team` Oder Bereich können mehrere `groupchat` Kontexte aufweisen.</span><span class="sxs-lookup"><span data-stu-id="14b27-120">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="14b27-121">Es folgen die Werte für die `context` Eigenschaft, aus der Sie alle oder einige der Werte verwenden können:</span><span class="sxs-lookup"><span data-stu-id="14b27-121">Following are the values for the `context` property from which you can use all or some of the values:</span></span>

|<span data-ttu-id="14b27-122">Wert</span><span class="sxs-lookup"><span data-stu-id="14b27-122">Value</span></span>|<span data-ttu-id="14b27-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14b27-123">Description</span></span>|
|---|---|
| <span data-ttu-id="14b27-124">**channelTab**</span><span class="sxs-lookup"><span data-stu-id="14b27-124">**channelTab**</span></span> | <span data-ttu-id="14b27-125">Eine Registerkarte in der Kopfzeile eines Teamkanals.</span><span class="sxs-lookup"><span data-stu-id="14b27-125">A tab in the header of a team channel.</span></span> |
| <span data-ttu-id="14b27-126">**privateChatTab**</span><span class="sxs-lookup"><span data-stu-id="14b27-126">**privateChatTab**</span></span> | <span data-ttu-id="14b27-127">Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung.</span><span class="sxs-lookup"><span data-stu-id="14b27-127">A tab in the header of a group chat between a set of users, not in the context of a team or meeting.</span></span> |
| <span data-ttu-id="14b27-128">**meetingChatTab**</span><span class="sxs-lookup"><span data-stu-id="14b27-128">**meetingChatTab**</span></span> | <span data-ttu-id="14b27-129">Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.</span><span class="sxs-lookup"><span data-stu-id="14b27-129">A tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span> |
| <span data-ttu-id="14b27-130">**meetingDetailsTab**</span><span class="sxs-lookup"><span data-stu-id="14b27-130">**meetingDetailsTab**</span></span> | <span data-ttu-id="14b27-131">Eine Registerkarte in der Kopfzeile der Besprechungsdetails-Ansicht des Kalenders.</span><span class="sxs-lookup"><span data-stu-id="14b27-131">A tab in the header of the meeting details view of the calendar.</span></span> |
| <span data-ttu-id="14b27-132">**meetingSidePanel**</span><span class="sxs-lookup"><span data-stu-id="14b27-132">**meetingSidePanel**</span></span> | <span data-ttu-id="14b27-133">Ein Besprechungsbereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="14b27-133">An in-meeting panel opened through the unified bar (U-bar).</span></span> |
| <span data-ttu-id="14b27-134">**meetingStage**</span><span class="sxs-lookup"><span data-stu-id="14b27-134">**meetingStage**</span></span> | <span data-ttu-id="14b27-135">Eine App aus dem meetingSidePanel kann für die Besprechungsphase freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="14b27-135">An app from the meetingSidePanel can be shared to the meeting stage.</span></span> |

> [!NOTE]
> <span data-ttu-id="14b27-136">`Context` auf mobilen Clients wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14b27-136">`Context` property is currently not supported on mobile clients.</span></span>

<span data-ttu-id="14b27-137">Nachdem Sie Ihre App für Teams Besprechungen aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="14b27-137">After you enable your app for Teams meetings, you must configure your app before a meeting, during a meeting, and after a meeting.</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="14b27-138">Konfigurieren Ihrer App für Besprechungsszenarien</span><span class="sxs-lookup"><span data-stu-id="14b27-138">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="14b27-139">Damit Ihre App im Registerkartenkatalog sichtbar ist, müssen konfigurierbare Registerkarten und der Gruppenchatbereich unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="14b27-139">For your app to be visible in the tab gallery, it must support configurable tabs and the group chat scope.</span></span>
> * <span data-ttu-id="14b27-140">Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen.</span><span class="sxs-lookup"><span data-stu-id="14b27-140">Mobile clients support tabs only in pre and post meeting stages.</span></span>
> * <span data-ttu-id="14b27-141">Die Besprechungsumgebungen, die sich im Dialogfeld "Besprechung" und "Registerkarte" befinden, werden derzeit auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14b27-141">The in-meeting experiences that is in-meeting dialog box and tab is currently not supported on mobile clients.</span></span> <span data-ttu-id="14b27-142">Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilgeräten,](../tabs/design/tabs-mobile.md) während Sie Ihre Registerkarten für mobilgeräte erstellen.</span><span class="sxs-lookup"><span data-stu-id="14b27-142">For more information, see [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) while creating your tabs for mobile.</span></span>

<span data-ttu-id="14b27-143">Teams Besprechungen bietet eine einzigartige Erfahrung für die Zusammenarbeit in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="14b27-143">Teams meetings provides a unique collaborative experience for your organization.</span></span> <span data-ttu-id="14b27-144">Es bietet die Möglichkeit, Ihre App für verschiedene Besprechungsszenarien zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="14b27-144">It provides the opportunity to configure your app for different meeting scenarios.</span></span> <span data-ttu-id="14b27-145">Sie können Ihre Apps so konfigurieren, dass die Besprechungserfahrung basierend auf der Teilnehmerrolle oder dem Benutzertyp verbessert wird.</span><span class="sxs-lookup"><span data-stu-id="14b27-145">You can configure your apps to enhance the meeting experience based on participant role or user type.</span></span> <span data-ttu-id="14b27-146">Jetzt können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ausgeführt werden können:</span><span class="sxs-lookup"><span data-stu-id="14b27-146">Now you can identify what actions can be taken in the following meeting scenarios:</span></span>
* [<span data-ttu-id="14b27-147">Vor der Besprechung</span><span class="sxs-lookup"><span data-stu-id="14b27-147">Pre-meeting</span></span>](#pre-meeting)
* [<span data-ttu-id="14b27-148">Besprechungsbesprechung</span><span class="sxs-lookup"><span data-stu-id="14b27-148">In-meeting</span></span>](#in-meeting)
* [<span data-ttu-id="14b27-149">Nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="14b27-149">Post-meeting</span></span>](#post-meeting)

### <a name="pre-meeting"></a><span data-ttu-id="14b27-150">Vor der Besprechung</span><span class="sxs-lookup"><span data-stu-id="14b27-150">Pre-meeting</span></span>

<span data-ttu-id="14b27-151">Vor einer Besprechung können Benutzer Registerkarten, Bots und Messaging-Erweiterungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="14b27-151">Before a meeting, users can add tabs, bots, and messaging extensions.</span></span> <span data-ttu-id="14b27-152">Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="14b27-152">Users with organizer and presenter roles can add tabs to a meeting.</span></span>

<span data-ttu-id="14b27-153">**So fügen Sie einer Besprechung eine Registerkarte hinzu**</span><span class="sxs-lookup"><span data-stu-id="14b27-153">**To add a tab to a meeting**</span></span>

1. <span data-ttu-id="14b27-154">Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="14b27-154">In your calendar, select a meeting to which you want to add a tab.</span></span>
1. <span data-ttu-id="14b27-155">Wählen Sie die Registerkarte **"Details"** aus, und wählen Sie</span><span class="sxs-lookup"><span data-stu-id="14b27-155">Select the **Details** tab and select</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="14b27-156">.</span><span class="sxs-lookup"><span data-stu-id="14b27-156">.</span></span>

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. <span data-ttu-id="14b27-158">Wählen Sie im daraufhin angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="14b27-158">In the tab gallery that appears, select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="14b27-159">Die App wird als Registerkarte installiert.</span><span class="sxs-lookup"><span data-stu-id="14b27-159">The app is installed as a tab.</span></span>

    > [!NOTE]
    > <span data-ttu-id="14b27-160">Derzeit wird das Abrufen von Besprechungsdetails und Teilnehmerinformationen auf der Registerkarte "Besprechungen" nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14b27-160">Currently, in meetings tab, getting meeting details and participant information is not supported.</span></span>

<span data-ttu-id="14b27-161">**So fügen Sie einer Besprechung eine Messaging-Erweiterung hinzu**</span><span class="sxs-lookup"><span data-stu-id="14b27-161">**To add a messaging extension to a meeting**</span></span>

1. <span data-ttu-id="14b27-162">Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; , die sich im Bereich zum Verfassen von Nachrichten im Chat befinden.</span><span class="sxs-lookup"><span data-stu-id="14b27-162">Select the ellipses &#x25CF;&#x25CF;&#x25CF; located in the compose message area in the chat.</span></span>
1. <span data-ttu-id="14b27-163">Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus.</span><span class="sxs-lookup"><span data-stu-id="14b27-163">Select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="14b27-164">Die App wird als Messaging-Erweiterung installiert.</span><span class="sxs-lookup"><span data-stu-id="14b27-164">The app is installed as a messaging extension.</span></span>

<span data-ttu-id="14b27-165">**So fügen Sie einer Besprechung einen Bot hinzu**</span><span class="sxs-lookup"><span data-stu-id="14b27-165">**To add a bot to a meeting**</span></span>

<span data-ttu-id="14b27-166">Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen **Sie "Bots abrufen" aus.**</span><span class="sxs-lookup"><span data-stu-id="14b27-166">In a meeting chat, enter the **@** key and select **Get bots**.</span></span>

> [!NOTE]
> * <span data-ttu-id="14b27-167">Die Benutzeridentität muss mit [tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden.</span><span class="sxs-lookup"><span data-stu-id="14b27-167">The user identity must be confirmed using [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="14b27-168">Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.</span><span class="sxs-lookup"><span data-stu-id="14b27-168">After authentication, the app can retrieve the user role using the `GetParticipant` API.</span></span>
> * <span data-ttu-id="14b27-169">Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="14b27-169">Based on the user role, the app has the capability to provide role specific experiences.</span></span> <span data-ttu-id="14b27-170">Eine Abruf-App ermöglicht beispielsweise nur Organisatoren und Referenten das Erstellen einer neuen Umfrage.</span><span class="sxs-lookup"><span data-stu-id="14b27-170">For example, a polling app allows only organizers and presenters to create a new poll.</span></span>
> * <span data-ttu-id="14b27-171">Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="14b27-171">Role assignments can be changed while a meeting is in progress.</span></span> <span data-ttu-id="14b27-172">Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="14b27-172">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

### <a name="in-meeting"></a><span data-ttu-id="14b27-173">Besprechungsbesprechung</span><span class="sxs-lookup"><span data-stu-id="14b27-173">In-meeting</span></span>

<span data-ttu-id="14b27-174">Während einer Besprechung können Sie das meetingSidePanel oder das Dialogfeld in der Besprechung verwenden, um einzigartige Umgebungen für Ihre Apps zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="14b27-174">During a meeting, you can use the meetingSidePanel or the in-meeting dialog box to build unique experiences for your apps.</span></span>

#### <a name="meetingsidepanel"></a><span data-ttu-id="14b27-175">meetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="14b27-175">meetingSidePanel</span></span>

<span data-ttu-id="14b27-176">Mit dem meetingSidePanel können Sie Benutzeroberflächen in einer Besprechung anpassen, die Organisatoren und Referenten unterschiedliche Ansichten und Aktionen ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="14b27-176">With the meetingSidePanel, you can customize experiences in a meeting that enable organizers and presenters to have different set of views and actions.</span></span> <span data-ttu-id="14b27-177">In Ihrem App-Manifest müssen Sie meetingSidePanel dem Kontextarray hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="14b27-177">In your app manifest, you must add meetingSidePanel to the context array.</span></span> <span data-ttu-id="14b27-178">In der Besprechung und in allen Szenarien wird die App auf einer Besprechungsregisterkarte mit einer Breite von 320 Pixeln gerendert.</span><span class="sxs-lookup"><span data-stu-id="14b27-178">In the meeting and in all scenarios, the app is rendered in an in-meeting tab that is 320 pixels in width.</span></span> <span data-ttu-id="14b27-179">Weitere Informationen finden Sie unter [FrameContext-Schnittstelle.](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="14b27-179">For more information, see [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).</span></span>

<span data-ttu-id="14b27-180">Informationen zur Verwendung der `userContext` API zum weiterleiten von Anforderungen finden Sie unter Teams [SDK.](../tabs/how-to/access-teams-context.md#user-context)</span><span class="sxs-lookup"><span data-stu-id="14b27-180">To use the `userContext` API to route requests accordingly, see [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span></span> <span data-ttu-id="14b27-181">Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Registerkarten.](../tabs/how-to/authentication/auth-flow-tab.md)</span><span class="sxs-lookup"><span data-stu-id="14b27-181">For more information, see [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="14b27-182">Der Authentifizierungsfluss für Registerkarten ist dem Authentifizierungsfluss für Websites sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="14b27-182">Authentication flow for tabs is very similar to the authentication flow for websites.</span></span> <span data-ttu-id="14b27-183">Registerkarten können daher OAuth 2.0 direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="14b27-183">So tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="14b27-184">Weitere Informationen finden Sie unter [Microsoft Identity Platform und OAuth 2.0-Autorisierungscodefluss.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)</span><span class="sxs-lookup"><span data-stu-id="14b27-184">For more information, see [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="14b27-185">Die Messaging-Erweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet und der Benutzer Erweiterungskarten zum Verfassen von Nachrichten posten kann.</span><span class="sxs-lookup"><span data-stu-id="14b27-185">Messaging extension works as expected when a user is in an in-meeting view, and the user can post compose message extension cards.</span></span> <span data-ttu-id="14b27-186">"AppName in-Meeting" ist eine QuickInfo, die den App-Namen in der Besprechungs-U-Leiste angibt.</span><span class="sxs-lookup"><span data-stu-id="14b27-186">AppName in-meeting is a tooltip that states the app name in-meeting U-bar.</span></span>

> [!NOTE]
> <span data-ttu-id="14b27-187">Verwenden Sie Version 1.7.0 oder höher von [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)da die vorherigen Versionen den Seitenbereich nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="14b27-187">Use version 1.7.0 or higher of [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), as versions prior to it do not support the side panel.</span></span>

#### <a name="in-meeting-dialog-box"></a><span data-ttu-id="14b27-188">Dialogfeld "Besprechungsinterne Besprechung"</span><span class="sxs-lookup"><span data-stu-id="14b27-188">In-meeting dialog box</span></span>

<span data-ttu-id="14b27-189">Das Dialogfeld in der Besprechung kann verwendet werden, um Teilnehmer während der Besprechung einzubeziehen und Während der Besprechung Informationen oder Feedback zu sammeln.</span><span class="sxs-lookup"><span data-stu-id="14b27-189">The in-meeting dialog box can be used to engage participants during the meeting and collect information or feedback during the meeting.</span></span> <span data-ttu-id="14b27-190">Verwenden Sie die [`NotificationSignal`](create-apps-for-teams-meetings.md#notificationsignal-api) API, um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="14b27-190">Use the [`NotificationSignal`](create-apps-for-teams-meetings.md#notificationsignal-api) API to signal that a bubble notification must be triggered.</span></span> <span data-ttu-id="14b27-191">Fügen Sie als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, unter der der anzuzeigende Inhalt gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="14b27-191">As part of the notification request payload, include the URL where the content to be shown is hosted.</span></span>

<span data-ttu-id="14b27-192">Das Besprechungsdialogfeld darf kein Aufgabenmodul verwenden.</span><span class="sxs-lookup"><span data-stu-id="14b27-192">In-meeting dialog must not use task module.</span></span> <span data-ttu-id="14b27-193">Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="14b27-193">Task module is not invoked in a meeting chat.</span></span> <span data-ttu-id="14b27-194">Eine externe Ressourcen-URL wird verwendet, um Inhaltsblase in einer Besprechung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="14b27-194">An external resource URL is used to display content bubble in a meeting.</span></span> <span data-ttu-id="14b27-195">Sie können die `submitTask` Methode verwenden, um Daten in einem Besprechungschat zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="14b27-195">You can use the `submitTask` method to submit data in a meeting chat.</span></span>

> [!NOTE]
> * <span data-ttu-id="14b27-196">Sie müssen die [SubmitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um sie automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="14b27-196">You must invoke the [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to dismiss automatically after a user takes an action in the web view.</span></span> <span data-ttu-id="14b27-197">Dies ist eine Anforderung für die App-Übermittlung.</span><span class="sxs-lookup"><span data-stu-id="14b27-197">This is a requirement for app submission.</span></span> <span data-ttu-id="14b27-198">Weitere Informationen finden Sie unter [Teams SDK-Aufgabenmodul.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="14b27-198">For more information, see [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
> * <span data-ttu-id="14b27-199">Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss ihre anfängliche Aufrufanforderungsnutzlast auf den `from.id` Anforderungsmetadaten im `from` Objekt basieren, nicht auf den `from.aadObjectId` Anforderungsmetadaten.</span><span class="sxs-lookup"><span data-stu-id="14b27-199">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id` request metadata in the `from` object, not the `from.aadObjectId` request metadata.</span></span> <span data-ttu-id="14b27-200">`from.id`ist die Benutzer-ID und `from.aadObjectId` die Azure Active Directory -ID (AAD) des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="14b27-200">`from.id` is the user ID and `from.aadObjectId` is the Azure Active Directory (AAD) ID of the user.</span></span> <span data-ttu-id="14b27-201">Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)</span><span class="sxs-lookup"><span data-stu-id="14b27-201">For more information, see [using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

#### <a name="share-to-stage"></a><span data-ttu-id="14b27-202">Freigeben in der Phase</span><span class="sxs-lookup"><span data-stu-id="14b27-202">Share to stage</span></span>

> [!NOTE]
> * <span data-ttu-id="14b27-203">Diese Funktion ist derzeit nur in der [Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="14b27-203">This capability is currently available in [developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>
> * <span data-ttu-id="14b27-204">Um dieses Feature zu verwenden, muss die App ein Besprechungs-MeetingSidePanel unterstützen.</span><span class="sxs-lookup"><span data-stu-id="14b27-204">To use this feature, the app must support an in-meeting meetingSidePanel.</span></span>

<span data-ttu-id="14b27-205">Diese Funktion bietet Entwicklern die Möglichkeit, eine App für die Besprechungsphase freizugeben.</span><span class="sxs-lookup"><span data-stu-id="14b27-205">This capability gives developers the ability to share an app to the meeting stage.</span></span> <span data-ttu-id="14b27-206">Durch Aktivieren der Freigabe für die Besprechungsphase können Besprechungsteilnehmer in Echtzeit zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="14b27-206">By enabling share to the meeting stage, meeting participants can collaborate in real-time.</span></span>

<span data-ttu-id="14b27-207">Der erforderliche Kontext befindet `meetingStage` sich im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="14b27-207">The required context is `meetingStage` in the app manifest.</span></span> <span data-ttu-id="14b27-208">Voraussetzung hierfür ist, dass der Kontext vorhanden `meetingSidePanel` ist.</span><span class="sxs-lookup"><span data-stu-id="14b27-208">A prerequisite for this is to have the `meetingSidePanel` context.</span></span> <span data-ttu-id="14b27-209">Dadurch wird **"Freigeben** im meetingSidePanel" aktiviert.</span><span class="sxs-lookup"><span data-stu-id="14b27-209">This enables **Share** in the meetingSidePanel.</span></span>

![Freigeben für die Bereitstellung während der Besprechungserfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

<span data-ttu-id="14b27-211">Die Manifeständerung, die zum Aktivieren dieser Funktion erforderlich ist, lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="14b27-211">The manifest change that is needed to enable this capability is as follows:</span></span>

```json
"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "groupchat"
      ],
      "context":[
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

### <a name="post-meeting"></a><span data-ttu-id="14b27-212">Nach der Besprechung</span><span class="sxs-lookup"><span data-stu-id="14b27-212">Post-meeting</span></span>

<span data-ttu-id="14b27-213">Die Konfigurationen nach der Besprechung und vor der [Besprechung](#pre-meeting) sind identisch.</span><span class="sxs-lookup"><span data-stu-id="14b27-213">The post-meeting and [pre-meeting](#pre-meeting) configurations are the same.</span></span>

## <a name="code-sample"></a><span data-ttu-id="14b27-214">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="14b27-214">Code sample</span></span>

|<span data-ttu-id="14b27-215">Beispielname</span><span class="sxs-lookup"><span data-stu-id="14b27-215">Sample name</span></span> | <span data-ttu-id="14b27-216">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14b27-216">Description</span></span> | <span data-ttu-id="14b27-217">Beispiel</span><span class="sxs-lookup"><span data-stu-id="14b27-217">Sample</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="14b27-218">Besprechungs-App</span><span class="sxs-lookup"><span data-stu-id="14b27-218">Meeting app</span></span> | <span data-ttu-id="14b27-219">Veranschaulicht, wie die Besprechungstoken-Generator-App verwendet wird, um ein Token anzufordern, das sequenziell generiert wird, damit jeder Teilnehmer eine angemessene Möglichkeit zur Interaktion hat.</span><span class="sxs-lookup"><span data-stu-id="14b27-219">Demonstrates how to use the Meeting Token Generator app to request a token, which is generated sequentially so that each participant has a fair opportunity to interact.</span></span> <span data-ttu-id="14b27-220">Dies kann in Situationen wie Meetings mit Derbesprechung, Q&A-Sitzungen usw. hilfreich sein.</span><span class="sxs-lookup"><span data-stu-id="14b27-220">This can be useful in situations like scrum meetings, Q&A sessions, and so on.</span></span> | [<span data-ttu-id="14b27-221">View</span><span class="sxs-lookup"><span data-stu-id="14b27-221">View</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token) |

## <a name="see-also"></a><span data-ttu-id="14b27-222">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="14b27-222">See also</span></span>

* [<span data-ttu-id="14b27-223">Entwurfsrichtlinien für Besprechungsdialoge</span><span class="sxs-lookup"><span data-stu-id="14b27-223">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="14b27-224">Teams Authentifizierungsfluss für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="14b27-224">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
