---
title: Entwerfen Ihrer App – Grundlegendes zur App-Struktur
description: Verstehen Sie, was Sie in Microsoft Teams beim Entwerfen Ihrer App anpassen können und was nicht.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: a574ebeb5416e614152bb24d52cc798f0032943c
ms.sourcegitcommit: 0fe60b3fd406a5768b18977df53d1f4c665e5300
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53133393"
---
# <a name="understand-the-microsoft-teams-app-structure"></a><span data-ttu-id="63ffa-103">Grundlegendes zur Microsoft Teams App-Struktur</span><span class="sxs-lookup"><span data-stu-id="63ffa-103">Understand the Microsoft Teams app structure</span></span>

<span data-ttu-id="63ffa-104">Beim Erstellen Ihrer App ist es wichtig zu wissen, was Sie in Microsoft Teams anpassen können und was nicht.</span><span class="sxs-lookup"><span data-stu-id="63ffa-104">When building your app, it's important to know what you can and can't customize in Microsoft Teams.</span></span> <span data-ttu-id="63ffa-105">Anhand dieser Informationen können Sie besser verstehen, welche Teile der App-Erfahrung Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="63ffa-105">This information can help you better understand which parts of the app experience you control.</span></span>

<span data-ttu-id="63ffa-106">Die folgenden Drahtframes zeigen Ihnen:</span><span class="sxs-lookup"><span data-stu-id="63ffa-106">The following wireframes show you:</span></span>

* <span data-ttu-id="63ffa-107">Die Oberflächen, die Sie in jeder Teams App-Funktion anpassen können (in Rosa umrissen).</span><span class="sxs-lookup"><span data-stu-id="63ffa-107">The surfaces you can customize in each Teams app capability (outlined in pink).</span></span>
* <span data-ttu-id="63ffa-108">Die Bereiche, die jede Funktion unterstützt.</span><span class="sxs-lookup"><span data-stu-id="63ffa-108">The scopes each capability supports.</span></span>

> [!TIP]
> <span data-ttu-id="63ffa-109">**Was bedeutet "Bereich"?**</span><span class="sxs-lookup"><span data-stu-id="63ffa-109">**What does scope mean?**</span></span> <span data-ttu-id="63ffa-110">Ein Bereich ist ein Bereich in Teams in dem Benutzer Ihre App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="63ffa-110">A scope is an area in Teams where people can use your app.</span></span> <span data-ttu-id="63ffa-111">Apps können einen oder mehrere Bereiche haben, einschließlich persönlich, Kanäle, Chats und Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="63ffa-111">Apps can have one or many scopes, including personal, channels, chats, and meetings.</span></span>

## <a name="personal-apps"></a><span data-ttu-id="63ffa-112">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="63ffa-112">Personal apps</span></span>

<span data-ttu-id="63ffa-113">Persönliche Apps bieten eine große Canvas, um Ihre App-Inhalte für einzelne Benutzer zu hosten.</span><span class="sxs-lookup"><span data-stu-id="63ffa-113">Personal apps provide a large canvas to host your app content for individual users.</span></span>

<span data-ttu-id="63ffa-114">***Unterstützte Bereiche:** Persönlich*</span><span class="sxs-lookup"><span data-stu-id="63ffa-114">\***Supported scopes**: Personal\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="63ffa-115">Desktop</span><span class="sxs-lookup"><span data-stu-id="63ffa-115">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="63ffa-116">Die Canvas ist ein iFrame, damit Sie die Benutzeroberfläche vollständig anpassen können.</span><span class="sxs-lookup"><span data-stu-id="63ffa-116">The canvas is an iframe so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf dem Desktop anpassen können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="63ffa-118">Mobil</span><span class="sxs-lookup"><span data-stu-id="63ffa-118">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="63ffa-119">Die Canvas ist eine Webansicht, mit der Sie die Benutzeroberfläche vollständig anpassen können.</span><span class="sxs-lookup"><span data-stu-id="63ffa-119">The canvas is a webview so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für persönliche Apps auf Mobilgeräten anpassen können." border="false":::

---

## <a name="tabs"></a><span data-ttu-id="63ffa-121">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="63ffa-121">Tabs</span></span>

<span data-ttu-id="63ffa-122">Registerkarten bieten einen großen Canvas zum Hosten der App-Inhalte für eine Gruppe von Benutzern.</span><span class="sxs-lookup"><span data-stu-id="63ffa-122">Tabs provide a large canvas to host your app content for a group of users.</span></span> <span data-ttu-id="63ffa-123">Sie können Registerkarten in freigegebene Bereiche wie Kanäle, Chats und Besprechungseinladungen einschließen.</span><span class="sxs-lookup"><span data-stu-id="63ffa-123">You can include tabs in shared spaces such as channels, chats, and meeting invites.</span></span>

<span data-ttu-id="63ffa-124">***Unterstützte Bereiche:** Kanäle, Chats, Besprechungen*</span><span class="sxs-lookup"><span data-stu-id="63ffa-124">\***Supported scopes**: Channels, Chats, Meetings\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="63ffa-125">Desktop</span><span class="sxs-lookup"><span data-stu-id="63ffa-125">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="63ffa-126">Die Canvas ist ein iFrame, damit Sie die Benutzeroberfläche vollständig anpassen können.</span><span class="sxs-lookup"><span data-stu-id="63ffa-126">The canvas is an iframe so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf Desktops anpassen können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="63ffa-128">Mobil</span><span class="sxs-lookup"><span data-stu-id="63ffa-128">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="63ffa-129">Die Canvas ist eine Webansicht, mit der Sie die Benutzeroberfläche vollständig anpassen können.</span><span class="sxs-lookup"><span data-stu-id="63ffa-129">The canvas is a webview so you can completely customize the experience.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Registerkarten auf Mobilgeräten anpassen können." border="false":::

---

## <a name="bots"></a><span data-ttu-id="63ffa-131">Bots</span><span class="sxs-lookup"><span data-stu-id="63ffa-131">Bots</span></span>

<span data-ttu-id="63ffa-132">Bots sind Unterhaltungs-Apps, die in Teams systemeigenen Messaging-Features integriert sind, sodass die Ui-Arbeit für Sie erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="63ffa-132">Bots are conversational apps that integrate with Teams native messaging features, so the UI work is handled for you.</span></span> <span data-ttu-id="63ffa-133">Aus Entwurfssicht gibt es weiterhin Möglichkeiten, Persönlichkeit, benutzerdefinierte Funktionen und umfangreiche, umsetzbare Informationen mit unserer NLP-Unterstützung (Natural Language Processing) und der Plattform für adaptive Karten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="63ffa-133">From a design standpoint, there are still opportunities to add personality, custom functionality, and rich, actionable information with our natural language processing (NLP) support and Adaptive Cards platform.</span></span>

<span data-ttu-id="63ffa-134">***Unterstützte Bereiche:** Persönlich, Kanäle, Chats, Besprechungen*</span><span class="sxs-lookup"><span data-stu-id="63ffa-134">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="63ffa-135">Desktop</span><span class="sxs-lookup"><span data-stu-id="63ffa-135">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf desktop anpassen können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="63ffa-137">Mobil</span><span class="sxs-lookup"><span data-stu-id="63ffa-137">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Bots auf Mobilen anpassen können." border="false":::

---

## <a name="messaging-extensions"></a><span data-ttu-id="63ffa-139">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="63ffa-139">Messaging extensions</span></span>

<span data-ttu-id="63ffa-140">Messagingerweiterungen sind Tastenkombinationen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne von der Konversation weg zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="63ffa-140">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span> <span data-ttu-id="63ffa-141">Action-based messaging extensions give you more control of the experience, while Teams handles much of what renders for search-based messaging extensions.</span><span class="sxs-lookup"><span data-stu-id="63ffa-141">Action-based messaging extensions give you more control of the experience, while Teams handles much of what renders for search-based messaging extensions.</span></span>

<span data-ttu-id="63ffa-142">***Unterstützte Bereiche:** Persönlich, Kanäle, Chats, Besprechungen*</span><span class="sxs-lookup"><span data-stu-id="63ffa-142">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="63ffa-143">Desktop</span><span class="sxs-lookup"><span data-stu-id="63ffa-143">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Messaging-Erweiterungen auf dem Desktop anpassen können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="63ffa-145">Mobil</span><span class="sxs-lookup"><span data-stu-id="63ffa-145">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Messaging-Erweiterungen auf mobilgeräten anpassen können." border="false":::

---

## <a name="meeting-extensions"></a><span data-ttu-id="63ffa-147">Besprechungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="63ffa-147">Meeting extensions</span></span>

<span data-ttu-id="63ffa-148">Besprechungserweiterungen sind Apps zur Verbesserung von Livebesprechungen.</span><span class="sxs-lookup"><span data-stu-id="63ffa-148">Meeting extensions are apps to enhance live meetings.</span></span> <span data-ttu-id="63ffa-149">Sie können Ihre App-Inhalte in verschiedenen Szenarien hosten, einschließlich vor, während und nach Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="63ffa-149">You can host your app content in several scenarios, including before, during, and after meetings.</span></span>

<span data-ttu-id="63ffa-150">***Unterstützte Bereiche:** Besprechungen, Chats*</span><span class="sxs-lookup"><span data-stu-id="63ffa-150">\***Supported scopes**: Meetings, Chats\*</span></span>

# <a name="desktop"></a>[<span data-ttu-id="63ffa-151">Desktop</span><span class="sxs-lookup"><span data-stu-id="63ffa-151">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="63ffa-152">Die Oberfläche ist ein iFrame, mit dem Sie die Benutzeroberfläche anpassen können. Bedenken Sie jedoch, dass diese Apps in Besprechungen dunkles Design verwenden und schmal sind.</span><span class="sxs-lookup"><span data-stu-id="63ffa-152">The surface is an iframe, allowing you to customize the experience, but keep in mind that during meetings these apps use dark theme and are narrow.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-desktop.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf dem Desktop anpassen können." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="63ffa-154">Mobil</span><span class="sxs-lookup"><span data-stu-id="63ffa-154">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="63ffa-155">Die Oberfläche ist eine Webansicht, mit der Sie die Benutzeroberfläche anpassen können. Bedenken Sie jedoch, dass diese Apps in Besprechungen dunkles Design verwenden.</span><span class="sxs-lookup"><span data-stu-id="63ffa-155">The surface is a webview, allowing you to customize the experience, but keep in mind that during meetings these apps use dark theme.</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions-mobile.png" alt-text="Konzeptionelle Abbildung der Front-End-Bereiche in Teams, die Entwickler für Besprechungserweiterungen auf mobilgeräten anpassen können." border="false":::

---
