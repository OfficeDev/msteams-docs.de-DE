---
title: Entwerfen Ihrer App – Verstehen der App-Struktur
description: Verstehen Sie, was Sie beim Entwerfen Ihrer App in Microsoft Teams anpassen können und nicht.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: surbhigupta
ms.openlocfilehash: bf84ad1d52cf46e9242bf4122dc5e900461ab806
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631310"
---
# <a name="understand-the-microsoft-teams-app-structure"></a><span data-ttu-id="b99dd-103">Verstehen der Microsoft Teams-App-Struktur</span><span class="sxs-lookup"><span data-stu-id="b99dd-103">Understand the Microsoft Teams app structure</span></span>

<span data-ttu-id="b99dd-104">Beim Erstellen Ihrer App ist es wichtig zu wissen, was Sie in der App Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b99dd-104">When building your app, it's important to know what you can and can't customize in Microsoft Teams.</span></span> <span data-ttu-id="b99dd-105">Diese Informationen helfen Ihnen, besser zu verstehen, welche Teile der App Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="b99dd-105">This information can help you better understand which parts of the app experience you control.</span></span>

<span data-ttu-id="b99dd-106">Die folgenden Wireframes zeigen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="b99dd-106">The following wireframes show you:</span></span>

* <span data-ttu-id="b99dd-107">Die Oberflächen, die Sie in den einzelnen apps Teams anpassen können (in Blau umrissen).</span><span class="sxs-lookup"><span data-stu-id="b99dd-107">The surfaces you can customize in each Teams app capability (outlined in blue).</span></span>
* <span data-ttu-id="b99dd-108">Die Bereiche, die jede Funktion unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b99dd-108">The scopes each capability supports.</span></span>

> [!NOTE]
> <span data-ttu-id="b99dd-109">**Was bedeutet Bereich?**</span><span class="sxs-lookup"><span data-stu-id="b99dd-109">**What does scope mean?**</span></span> <span data-ttu-id="b99dd-110">Ein Bereich ist ein Bereich in Teams, in dem Benutzer Ihre App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="b99dd-110">A scope is an area in Teams where people can use your app.</span></span> <span data-ttu-id="b99dd-111">Apps können einen oder mehrere Bereiche haben, einschließlich persönlicher, Kanäle, Chats und Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="b99dd-111">Apps can have one or many scopes, including personal, channels, chats, and meetings.</span></span>

## <a name="personal-apps"></a><span data-ttu-id="b99dd-112">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="b99dd-112">Personal apps</span></span>

<span data-ttu-id="b99dd-113">Persönliche Apps bieten eine große Canvas, um Ihre App-Inhalte für einzelne Benutzer zu hosten.</span><span class="sxs-lookup"><span data-stu-id="b99dd-113">Personal apps provide a large canvas to host your app content for individual users.</span></span> <span data-ttu-id="b99dd-114">Der Zeichenbereich ist ein iframe, damit Sie die Benutzererfahrung vollständig anpassen können.</span><span class="sxs-lookup"><span data-stu-id="b99dd-114">The canvas is an iframe so you can completely customize the experience.</span></span>

<span data-ttu-id="b99dd-115">\***Unterstützte Bereiche**: Persönlich\*</span><span class="sxs-lookup"><span data-stu-id="b99dd-115">\***Supported scopes**: Personal\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-personal-apps.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für persönliche Apps anpassen können." border="false":::

## <a name="tabs"></a><span data-ttu-id="b99dd-117">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="b99dd-117">Tabs</span></span>

<span data-ttu-id="b99dd-118">Registerkarten bieten eine große Canvas zum Hosten von App-Inhalten für eine Gruppe von Benutzern.</span><span class="sxs-lookup"><span data-stu-id="b99dd-118">Tabs provide a large canvas to host your app content for a group of users.</span></span> <span data-ttu-id="b99dd-119">Sie können Registerkarten in freigegebene Bereiche wie Kanäle, Chats und Besprechungs einladen.</span><span class="sxs-lookup"><span data-stu-id="b99dd-119">You can include tabs in shared spaces such as channels, chats, and meeting invites.</span></span> <span data-ttu-id="b99dd-120">Der Zeichenbereich ist ein iframe, damit Sie die Benutzererfahrung vollständig anpassen können.</span><span class="sxs-lookup"><span data-stu-id="b99dd-120">The canvas is an iframe so you can completely customize the experience.</span></span>

<span data-ttu-id="b99dd-121">\***Unterstützte Bereiche**: Kanäle, Chats, Besprechungen\*</span><span class="sxs-lookup"><span data-stu-id="b99dd-121">\***Supported scopes**: Channels, Chats, Meetings\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-tabs.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Registerkarten anpassen können." border="false":::

## <a name="bots"></a><span data-ttu-id="b99dd-123">Bots</span><span class="sxs-lookup"><span data-stu-id="b99dd-123">Bots</span></span>

<span data-ttu-id="b99dd-124">Bots sind Unterhaltungs-Apps, die Teams systemeigenen Messagingfeatures integrieren, sodass die Benutzeroberflächenarbeit für Sie erledigt wird.</span><span class="sxs-lookup"><span data-stu-id="b99dd-124">Bots are conversational apps that integrate with Teams native messaging features, so the UI work is handled for you.</span></span> <span data-ttu-id="b99dd-125">Aus entwurfsspezifischer Sicht gibt es weiterhin Möglichkeiten, persönlichkeitsspezifische, benutzerdefinierte Funktionen und umfangreiche, umsetzbare Informationen mit unserer Unterstützung für die Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP) und der Adaptive Cards-Plattform hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b99dd-125">From a design standpoint, there are still opportunities to add personality, custom functionality, and rich, actionable information with our natural language processing (NLP) support and Adaptive Cards platform.</span></span>

<span data-ttu-id="b99dd-126">\***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen\*</span><span class="sxs-lookup"><span data-stu-id="b99dd-126">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-bots.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Bots anpassen können." border="false":::

## <a name="messaging-extensions"></a><span data-ttu-id="b99dd-128">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b99dd-128">Messaging extensions</span></span>

<span data-ttu-id="b99dd-129">Messagingerweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln in einer Nachricht, ohne aus der Unterhaltung zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="b99dd-129">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span> <span data-ttu-id="b99dd-130">Aktionsbasierte Messagingerweiterungen bieten Ihnen mehr Kontrolle über die Besensung, während Teams vieles von dem verarbeitet, was für suchbasierte Messagingerweiterungen gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="b99dd-130">Action-based messaging extensions give you more control of the experience, while Teams handles much of what renders for search-based messaging extensions.</span></span>

<span data-ttu-id="b99dd-131">\***Unterstützte Bereiche**: Persönlich, Kanäle, Chats, Besprechungen\*</span><span class="sxs-lookup"><span data-stu-id="b99dd-131">\***Supported scopes**: Personal, Channels, Chats, Meetings\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-messaging-exetensions.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Messagingerweiterungen anpassen können." border="false":::

## <a name="meeting-extensions"></a><span data-ttu-id="b99dd-133">Besprechungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="b99dd-133">Meeting extensions</span></span>

<span data-ttu-id="b99dd-134">Besprechungserweiterungen sind Apps zur Verbesserung von Livebesprechungen.</span><span class="sxs-lookup"><span data-stu-id="b99dd-134">Meeting extensions are apps to enhance live meetings.</span></span> <span data-ttu-id="b99dd-135">Sie können Ihre App-Inhalte in verschiedenen Szenarien hosten, z. B. vor, während und nach Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="b99dd-135">You can host your app content in several scenarios, including before, during, and after meetings.</span></span> <span data-ttu-id="b99dd-136">Die Oberfläche ist ein iframe, mit dem Sie die Oberfläche anpassen können, beachten Sie jedoch, dass diese Apps dunkel und schmal in Besprechungen sind.</span><span class="sxs-lookup"><span data-stu-id="b99dd-136">The surface is an iframe, allowing you to customize the experience, but keep in mind that these apps are dark themed and narrow during meetings.</span></span>

<span data-ttu-id="b99dd-137">\***Unterstützte Bereiche**: Besprechungen, Chats\*</span><span class="sxs-lookup"><span data-stu-id="b99dd-137">\***Supported scopes**: Meetings, Chats\*</span></span>

:::image type="content" source="../../assets/images/design-guidelines/app-structure-meeting-exetensions.png" alt-text="Konzeptionelle Abbildung mit den Front-End-Bereichen in Teams, die Entwickler für Besprechungserweiterungen anpassen können." border="false":::
