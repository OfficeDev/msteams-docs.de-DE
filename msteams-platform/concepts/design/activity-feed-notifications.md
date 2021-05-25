---
title: Entwerfen von Aktivitätsfeedbenachrichtigungen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aktivitätsfeedbenachrichtigungen für Ihre Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 61a2a6da2a5ed0cb3126b9798094b06c575c9b6c
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631290"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a><span data-ttu-id="9fecf-103">Entwerfen von Aktivitätsfeedbenachrichtigungen für Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="9fecf-103">Designing activity feed notifications for your Microsoft Teams app</span></span>

<span data-ttu-id="9fecf-104">Der Aktivitätsfeed ist eine Oberfläche, auf die Benutzer auf ihre Benachrichtigungen in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9fecf-104">The activity feed is a surface for users to access their notifications in Microsoft Teams.</span></span> <span data-ttu-id="9fecf-105">Der Feed behält Benachrichtigungen aus den letzten vier Wochen bei.</span><span class="sxs-lookup"><span data-stu-id="9fecf-105">The feed retains notifications from the past four weeks.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="9fecf-106">Desktop</span><span class="sxs-lookup"><span data-stu-id="9fecf-106">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="Beispiel zeigt eine App-Benachrichtigung, die im Teams angezeigt wird." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="9fecf-108">Mobil</span><span class="sxs-lookup"><span data-stu-id="9fecf-108">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="Beispiel zeigt eine App-Benachrichtigung, die im Teams-Aktivitätsfeed auf Mobilgeräten angezeigt wird." border="false":::

---

## <a name="anatomy"></a><span data-ttu-id="9fecf-110">Anatomie</span><span class="sxs-lookup"><span data-stu-id="9fecf-110">Anatomy</span></span>

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Designanatomie der Teams Aktivitätsfeedbenachrichtigung." border="false":::

|<span data-ttu-id="9fecf-112">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="9fecf-112">Counter</span></span>|<span data-ttu-id="9fecf-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fecf-113">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="9fecf-114">1</span><span class="sxs-lookup"><span data-stu-id="9fecf-114">1</span></span>|<span data-ttu-id="9fecf-115">**Avatar**: Zeigt an, wer die Aktivität initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="9fecf-115">**Avatar**: Shows who initiated the activity.</span></span>|
|<span data-ttu-id="9fecf-116">2</span><span class="sxs-lookup"><span data-stu-id="9fecf-116">2</span></span>|<span data-ttu-id="9fecf-117">**Aktivitätstyp/App-Symbol**: Zeigt den Aktivitätstyp an.</span><span class="sxs-lookup"><span data-stu-id="9fecf-117">**Activity type/app icon**: Depicts the type of activity.</span></span> <span data-ttu-id="9fecf-118">Bei App-Benachrichtigungen wird das Liniensymbol durch ein App-Symbol ersetzt.</span><span class="sxs-lookup"><span data-stu-id="9fecf-118">For app notifications, the line icon is replaced with an app icon.</span></span>|
|<span data-ttu-id="9fecf-119">3</span><span class="sxs-lookup"><span data-stu-id="9fecf-119">3</span></span>|<span data-ttu-id="9fecf-120">**Titel (erste Zeile): Actor + Grund**: *Actor*: Name des Benutzers oder der App, der die Aktivität initiiert hat.</span><span class="sxs-lookup"><span data-stu-id="9fecf-120">**Title (first line): Actor + reason**: *Actor*: Name of the user or app that initiated the activity.</span></span> <span data-ttu-id="9fecf-121">*Grund*: Beschreibt die Aktivität.</span><span class="sxs-lookup"><span data-stu-id="9fecf-121">*Reason*: Describes the activity.</span></span>|
|<span data-ttu-id="9fecf-122">4 </span><span class="sxs-lookup"><span data-stu-id="9fecf-122">4</span></span>|<span data-ttu-id="9fecf-123">**Zeitstempel**: Zeigt an, wann die Aktivität passiert ist.</span><span class="sxs-lookup"><span data-stu-id="9fecf-123">**Timestamp**: Shows when the activity happened.</span></span>|
|<span data-ttu-id="9fecf-124">5 </span><span class="sxs-lookup"><span data-stu-id="9fecf-124">5</span></span>|<span data-ttu-id="9fecf-125">**Position (zweite Zeile):** Zeigt an, wo die Aktivität in der Teams.</span><span class="sxs-lookup"><span data-stu-id="9fecf-125">**Location (second line)**: Shows where the activity happened in Teams.</span></span>|
|<span data-ttu-id="9fecf-126">6 </span><span class="sxs-lookup"><span data-stu-id="9fecf-126">6</span></span>|<span data-ttu-id="9fecf-127">**Tertiäre Informationen (dritte Zeile):** Optional.</span><span class="sxs-lookup"><span data-stu-id="9fecf-127">**Tertiary information (third line)**: Optional.</span></span> <span data-ttu-id="9fecf-128">Zeigt Vorschautext oder zusätzliche Informationen an.</span><span class="sxs-lookup"><span data-stu-id="9fecf-128">Shows preview text or additional information.</span></span>|

## <a name="types-of-activity-feed-notification-cards"></a><span data-ttu-id="9fecf-129">Typen von Aktivitätsfeedbenachrichtigungskarten</span><span class="sxs-lookup"><span data-stu-id="9fecf-129">Types of activity feed notification cards</span></span>

<span data-ttu-id="9fecf-130">Die folgenden Varianten zeigen die Arten von Aktivitätsfeedbenachrichtigungskarten, die Sie anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="9fecf-130">The following variants show the kinds of activity feed notification cards you can display.</span></span> <span data-ttu-id="9fecf-131">Das App-Logo ersetzt den Benutzer-Avatar für app-generierte Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="9fecf-131">The app logo replaces the user avatar for app-generated notifications.</span></span>

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Varianten Teams Aktivitätsfeedkarten." border="false":::

## <a name="manage-activity-feed-notifications"></a><span data-ttu-id="9fecf-133">Verwalten von Aktivitätsfeedbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="9fecf-133">Manage activity feed notifications</span></span>

<span data-ttu-id="9fecf-134">Benutzer können Benachrichtigungen, die von Ihrer App gesendet werden, auf der Seite Teams verwalten.</span><span class="sxs-lookup"><span data-stu-id="9fecf-134">Users can manage notifications sent from your app in the Teams settings page.</span></span>

## <a name="related-system-notifications"></a><span data-ttu-id="9fecf-135">Verwandte Systembenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="9fecf-135">Related system notifications</span></span>

<span data-ttu-id="9fecf-136">Jede Aktivität generiert eine Systembenachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="9fecf-136">Each activity generates a system notification.</span></span> <span data-ttu-id="9fecf-137">Was angezeigt wird, hängt davon ab, was der Benutzer in seinen Benachrichtigungseinstellungen konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="9fecf-137">What displays depends on what the user configures in their notification settings.</span></span> <span data-ttu-id="9fecf-138">Benutzer können auch eine Benachrichtigungsart basierend auf ihrem Betriebssystem auswählen.</span><span class="sxs-lookup"><span data-stu-id="9fecf-138">Users can also choose a notification style based on their operating system.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="9fecf-139">Desktop</span><span class="sxs-lookup"><span data-stu-id="9fecf-139">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Varianten von Teams Aktivitätskarten auf verschiedenen Betriebssystemen." border="false":::

|<span data-ttu-id="9fecf-141">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="9fecf-141">Counter</span></span>|<span data-ttu-id="9fecf-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fecf-142">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="9fecf-143">1</span><span class="sxs-lookup"><span data-stu-id="9fecf-143">1</span></span>|<span data-ttu-id="9fecf-144">Teams benutzerdefinierte</span><span class="sxs-lookup"><span data-stu-id="9fecf-144">Teams custom</span></span>|
|<span data-ttu-id="9fecf-145">2</span><span class="sxs-lookup"><span data-stu-id="9fecf-145">2</span></span>|<span data-ttu-id="9fecf-146">Windows</span><span class="sxs-lookup"><span data-stu-id="9fecf-146">Windows</span></span>|
|<span data-ttu-id="9fecf-147">3</span><span class="sxs-lookup"><span data-stu-id="9fecf-147">3</span></span>|<span data-ttu-id="9fecf-148">Mac</span><span class="sxs-lookup"><span data-stu-id="9fecf-148">Mac</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="9fecf-149">Mobil</span><span class="sxs-lookup"><span data-stu-id="9fecf-149">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Varianten Teams Aktivitätsfeedkarten unter Android und iOS." border="false":::

|<span data-ttu-id="9fecf-151">Leistungsindikator</span><span class="sxs-lookup"><span data-stu-id="9fecf-151">Counter</span></span>|<span data-ttu-id="9fecf-152">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9fecf-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="9fecf-153">1</span><span class="sxs-lookup"><span data-stu-id="9fecf-153">1</span></span>|<span data-ttu-id="9fecf-154">Android</span><span class="sxs-lookup"><span data-stu-id="9fecf-154">Android</span></span>|
|<span data-ttu-id="9fecf-155">2</span><span class="sxs-lookup"><span data-stu-id="9fecf-155">2</span></span>|<span data-ttu-id="9fecf-156">iOS</span><span class="sxs-lookup"><span data-stu-id="9fecf-156">iOS</span></span>|

---

## <a name="next-step"></a><span data-ttu-id="9fecf-157">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="9fecf-157">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9fecf-158">Implementieren von Aktivitätsfeedbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="9fecf-158">Implement activity feed notifications</span></span>](/graph/teams-send-activityfeednotifications)
