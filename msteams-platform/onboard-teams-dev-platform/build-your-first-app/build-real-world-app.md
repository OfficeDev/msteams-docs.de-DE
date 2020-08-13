---
title: Erstellen Ihrer ersten Teams-App
author: heath-hamilton
description: Lernprogramm zum Erstellen einer Microsoft Teams-app in einer realen Welt
ms.openlocfilehash: 4915dde4ef5a852f4fc5d1e4c83e3349db2eaf6b
ms.sourcegitcommit: 80bf79a952bb14cbc38c0bd1e3cf8a346158e28e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "46655674"
---
# <a name="learn-how-to-build-your-first-teams-app"></a><span data-ttu-id="5499d-103">Erfahren Sie, wie Sie Ihre erste Teams-app erstellen</span><span class="sxs-lookup"><span data-stu-id="5499d-103">Learn how to build your first Teams app</span></span>

<span data-ttu-id="5499d-104">In **Erstellen Ihrer ersten App**erfahren Sie, wie Sie mithilfe von Lernprogrammen eine einfache Teams-app erstellen.</span><span class="sxs-lookup"><span data-stu-id="5499d-104">In **Build your first app**, you learn how to create a basic Teams app through tutorials.</span></span> <span data-ttu-id="5499d-105">Die Lektionen bauen auf einander auf und führen Sie durch jeden Schritt der Erstellung einer einfachen Real-World Teams-app.</span><span class="sxs-lookup"><span data-stu-id="5499d-105">The lessons build on each other, walking you through each step of creating a simple, real-world Teams app.</span></span> <span data-ttu-id="5499d-106">Wir stellen Ihnen allgemeine Tools, grundlegende Konzepte und nützliche Links auf dem Weg vor.</span><span class="sxs-lookup"><span data-stu-id="5499d-106">We introduce you to common tools, fundamental concepts, and useful links along the way.</span></span>

<span data-ttu-id="5499d-107">Beginnen Sie mit der Erstellung und Ausführung eines "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="5499d-107">You'll start with creating and running a "Hello, World!"</span></span> <span data-ttu-id="5499d-108">Tab-app.</span><span class="sxs-lookup"><span data-stu-id="5499d-108">tab app.</span></span> <span data-ttu-id="5499d-109">Anschließend erstellen Sie eine einfache Benutzeroberfläche und erfahren, wie Sie mit Microsoft Teams JavaScript SDK nützliche Kontexte erhalten.</span><span class="sxs-lookup"><span data-stu-id="5499d-109">You'll then create some simple UI and learn how to get useful context with the Microsoft Teams Javascript SDK.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="5499d-110">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="5499d-110">What you'll learn</span></span>

> [!div class="checklist"]
  >
  > - <span data-ttu-id="5499d-111">Mit dem Microsoft Teams Toolkit für Visual Studio Code können Sie **schnell mit dem Team-Toolkit in Kontakt**treten, um ein App-Projekt und ein Gerüst zu erstellen, damit Sie in wenigen Minuten eine laufende APP haben.</span><span class="sxs-lookup"><span data-stu-id="5499d-111">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > - <span data-ttu-id="5499d-112">**Definieren Sie Ihre APP mit dem Manifest**: das Manifest ist ein Blueprint, in dem Sie die Funktionen und Dienste angeben, die ihre Teams-App verwendet.</span><span class="sxs-lookup"><span data-stu-id="5499d-112">**Define your app with the manifest**: The manifest is a blueprint where you specify the capabilities and services your Teams app uses.</span></span>
  > - <span data-ttu-id="5499d-113">**Bereich Ihrer Zielgruppe**: Sie können eine Teams-App für den persönlichen Gebrauch oder die Zusammenarbeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="5499d-113">**Scope your audience**: You can build a Teams app for personal use or collaboration.</span></span> <span data-ttu-id="5499d-114">In den Lernprogrammen erfahren Sie, wie Sie eine Registerkarte für einzelne Benutzer oder eine Gruppe von Personen in einem Kanal oder Chat erstellen.</span><span class="sxs-lookup"><span data-stu-id="5499d-114">In the tutorials, you'll learn how build a tab for individual users or a group of people in a channel or chat.</span></span>
  > - <span data-ttu-id="5499d-115">Verwenden von Microsoft Teams **SDK zum Abrufen von Kontexten**: Hier erfahren Sie, wie Sie das Microsoft Teams-JavaScript-SDK zum Ausführen von Designänderungen oder zum Einrichten der Konfigurationsumgebung verwenden.</span><span class="sxs-lookup"><span data-stu-id="5499d-115">**Utilize Teams SDK to get context**: Learn how to use the Microsoft Teams JavaScript SDK to perform theme change or set up configuration experience</span></span>  
  > - <span data-ttu-id="5499d-116">**Erweitern Sie Ihre APP**: in den Lernprogrammen wird auf Verwandte Themen eingelinkt, die Sie wahrscheinlich interessieren (darunter auch Authentifizierungs-und Entwurfsrichtlinien).</span><span class="sxs-lookup"><span data-stu-id="5499d-116">**Expand on your app**: Throughout the tutorials, we link to related topics you're probably interested in (some of which include authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="5499d-117">Grundlagen der Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="5499d-117">Teams app fundamentals</span></span>

<span data-ttu-id="5499d-118">Bevor Sie mit den Lernprogrammen beginnen, sollten Sie die folgenden Informationen zum Erstellen von Apps für Microsoft Teams kennen.</span><span class="sxs-lookup"><span data-stu-id="5499d-118">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities"></a><span data-ttu-id="5499d-119">Apps können mehrere Funktionen haben</span><span class="sxs-lookup"><span data-stu-id="5499d-119">Apps can have multiple capabilities</span></span>

<span data-ttu-id="5499d-120">Microsoft Teams-apps bestehen aus einer oder mehreren [Plattformfunktionen](../capabilities-overview.md), einschließlich [Registerkarten](../doc-links/what-are-tabs.md), [Bots](../doc-links/what-are-bots.md ), [Messaging Erweiterungen](../doc-links/what-are-messaging-extensions.md)und [webhooks und Connectors](../doc-links/what-are-webhooks-and-connectors.md).</span><span class="sxs-lookup"><span data-stu-id="5499d-120">Teams apps are made up of one or more [platform capabilities](../capabilities-overview.md), including [tabs](../doc-links/what-are-tabs.md), [bots](../doc-links/what-are-bots.md ), [messaging extensions](../doc-links/what-are-messaging-extensions.md), and [webhooks and connectors](../doc-links/what-are-webhooks-and-connectors.md).</span></span> <span data-ttu-id="5499d-121">Microsoft Teams-apps weisen auch viele Benutzer [Oberflächen Konventionen und-Elemente](../doc-links/teams-ui-conventions.md)wie Karten, Aufgaben Module und Deep Linking auf, mit denen Sie die bestmögliche Benutzererfahrung erstellen können.</span><span class="sxs-lookup"><span data-stu-id="5499d-121">Teams apps also have many [UI conventions and elements](../doc-links/teams-ui-conventions.md), such as cards, task modules, and deep linking, you can use to build the best possible user experience.</span></span>

<span data-ttu-id="5499d-122">Für diese Lernprogramme erstellen Sie nur Registerkarten, können Ihrer APP jedoch einen bot oder eine andere Funktion hinzufügen, wie Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="5499d-122">For these tutorials, you'll build only tabs but can add a bot or other capability to your app as you like.</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="5499d-123">Ihre APP wird von Microsoft Teams nicht gehostet.</span><span class="sxs-lookup"><span data-stu-id="5499d-123">Teams doesn't host your app</span></span>  

<span data-ttu-id="5499d-124">Eine Teams-App besteht aus drei Hauptteilen:</span><span class="sxs-lookup"><span data-stu-id="5499d-124">A Teams app consists of three major pieces:</span></span>

1. <span data-ttu-id="5499d-125">Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="5499d-125">The Microsoft Teams client (web, desktop, or mobile) where users interact with your app.</span></span>
1. <span data-ttu-id="5499d-126">Ihre APP, Ihr Dienst, Ihr Workflow oder Ihre Website, die die erforderliche Logik, Datenspeicherung und API-Aufrufe ausführt, um Ihre APP zu vertreiben.</span><span class="sxs-lookup"><span data-stu-id="5499d-126">Your app, service, workflow, or website that performs the necessary logic, data storage, and API calls to power your app.</span></span>
1. <span data-ttu-id="5499d-127">Ihr App-Paket, mit dem Sie die app in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="5499d-127">Your app package, which you use to install the app in Teams.</span></span> <span data-ttu-id="5499d-128">Sie enthält App-Metadaten (Name, Symbole usw.) und Zeiger auf ihre Dienste.</span><span class="sxs-lookup"><span data-stu-id="5499d-128">It contains app metadata (name, icons, etc.) and pointers to your services.</span></span>

## <a name="next-step"></a><span data-ttu-id="5499d-129">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="5499d-129">Next step</span></span>

<span data-ttu-id="5499d-130">Das ist alles für jetzt, Let es Get Started!</span><span class="sxs-lookup"><span data-stu-id="5499d-130">That's all for now, let's get started!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5499d-131">Erstellen und Ausführen ihrer ersten App</span><span class="sxs-lookup"><span data-stu-id="5499d-131">Build and run your first app</span></span>](build-and-run-with-toolkit.md)
