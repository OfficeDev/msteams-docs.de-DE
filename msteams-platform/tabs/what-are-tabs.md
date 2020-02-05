---
title: Was sind benutzerdefinierte Registerkarten in Microsoft Teams?
author: laujan
description: Eine Übersicht über benutzerdefinierte Registerkarten auf der Microsoft Teams-Plattform
ms.topic: overview
ms.author: v-laujan
ms.openlocfilehash: 7560a9a7d19ca0182b2f5f45b304a96a0f2dddd4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674528"
---
# <a name="what-are-microsoft-teams-custom-tabs"></a><span data-ttu-id="20f6e-103">Was sind benutzerdefinierte Microsoft Teams-Registerkarten?</span><span class="sxs-lookup"><span data-stu-id="20f6e-103">What are Microsoft Teams custom tabs?</span></span>

<span data-ttu-id="20f6e-104">Registerkarten sind Teams-fähige Webseiten, die in Microsoft Teams eingebettet sind.</span><span class="sxs-lookup"><span data-stu-id="20f6e-104">Tabs are Teams-aware webpages embedded in Microsoft Teams.</span></span> <span data-ttu-id="20f6e-105">Sie können als Teil eines Kanals innerhalb eines Teams, eines Gruppenchats oder als persönliche App für einen einzelnen Benutzer hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="20f6e-105">They can be added as part of a channel inside a team, a group chat or as a personal app for an individual user.</span></span> <span data-ttu-id="20f6e-106">Als Teil ihrer App können Sie benutzerdefinierte Registerkarten hinzufügen, um Ihre eigenen Webinhalte in Microsoft Teams einzubetten und mit dem [JavaScript-Client-SDK von Teams](/javascript/api/overview/msteams-client)Ihrem Webinhalt Teams-spezifische Funktionen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="20f6e-106">As part of your app you can add custom tabs to embed your own web content in Teams, and using the [Teams JavaScript client SDK](/javascript/api/overview/msteams-client), add Teams-specific functionality to your web content.</span></span>

> [!NOTE]
> <span data-ttu-id="20f6e-107">In Chrome 80, das für die Veröffentlichung Anfang 2020 vorgesehen ist, werden neue Cookiewerte eingeführt und standardmäßig Cookie-Richtlinien auferlegt.</span><span class="sxs-lookup"><span data-stu-id="20f6e-107">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="20f6e-108">Es wird empfohlen, dass Sie die vorgesehene Verwendung für Ihre Cookies festlegen, anstatt sich auf das Standardbrowser Verhalten zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="20f6e-108">It's recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="20f6e-109">*Siehe* [SameSite-Cookie-Attribut (2020 Update)](../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="20f6e-109">*See* [SameSite cookie attribute (2020 update)](../resources/samesite-cookie-update.md).</span></span>

<span data-ttu-id="20f6e-110">Es gibt zwei Arten von Registerkarten in Microsoft Teams – Kanal/Gruppe und persönlich.</span><span class="sxs-lookup"><span data-stu-id="20f6e-110">There are two types of tabs available in Teams - channel/group and personal.</span></span> <span data-ttu-id="20f6e-111">Eine Kanal-Gruppe-Registerkarte bietet Inhalte für Kanäle und Gruppenchats und ist eine hervorragende Möglichkeit zum Erstellen von kollaborativen Räumen um dedizierte webbasierte Inhalte.</span><span class="sxs-lookup"><span data-stu-id="20f6e-111">A channel/group tab delivers content to channels and group chats, and are a great way to create collaborative spaces around dedicated web-based content.</span></span> <span data-ttu-id="20f6e-112">Persönliche Registerkarten, zusammen mit personenbezogenen Bots, gehören zu persönlichen apps und sind für einen einzelnen Benutzer ausgelegt.</span><span class="sxs-lookup"><span data-stu-id="20f6e-112">Personal tabs, along with personally-scoped bots, are part of personal apps and are scoped to a single user.</span></span> <span data-ttu-id="20f6e-113">Sie können für einfachen Zugriff an der linken Navigationsleiste fixiert werden.</span><span class="sxs-lookup"><span data-stu-id="20f6e-113">They can be pinned to the left navigation bar for easy access.</span></span>

## <a name="tabs-user-scenarios"></a><span data-ttu-id="20f6e-114">Benutzerszenarien für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="20f6e-114">Tabs user scenarios</span></span>

<span data-ttu-id="20f6e-115">**Szenario:** Bereitstelleneiner vorhandenen webbasierten Ressource in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="20f6e-115">**Scenario:** Bring an existing web-based resource inside Teams.</span></span> \
<span data-ttu-id="20f6e-116">**Beispiel:** Sie erstellen eine persönliche Registerkarte in Ihrer Teams-APP, die Benutzern eine Informations-Unternehmenswebsite zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="20f6e-116">**Example:** You create a personal tab in your Teams app that presents an informational corporate website to users.</span></span>

<span data-ttu-id="20f6e-117">**Szenario:** Hinzufügen von Support Seiten zu einem Teams-bot oder einer Messaging Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="20f6e-117">**Scenario:** Add support pages to a Teams bot or messaging extension.</span></span> \
<span data-ttu-id="20f6e-118">**Beispiel:** Sie erstellen persönliche Registerkarten, die Webseiteninhalte für Benutzer bereitstellen und Ihnen helfen.</span><span class="sxs-lookup"><span data-stu-id="20f6e-118">**Example:** You create personal tabs that provide about and help webpage content to users.</span></span>

<span data-ttu-id="20f6e-119">**Szenario:** Bereitstellen des Zugriffs auf Elemente, mit denen Ihre Benutzer regelmäßig für kooperativen Dialog und Zusammenarbeit interagieren.</span><span class="sxs-lookup"><span data-stu-id="20f6e-119">**Scenario:** Provide access to items that your users interact with regularly for cooperative dialogue and collaboration.</span></span> \
<span data-ttu-id="20f6e-120">**Beispiel:** Sie erstellen eine Kanal-Gruppe-Registerkarte mit einer tiefen Verknüpfung mit einzelnen Elementen.</span><span class="sxs-lookup"><span data-stu-id="20f6e-120">**Example:** You create a channel/group tab with deep linking to individual items.</span></span>

## <a name="how-do-tabs-work"></a><span data-ttu-id="20f6e-121">Wie funktionieren Registerkarten?</span><span class="sxs-lookup"><span data-stu-id="20f6e-121">How do tabs work?</span></span>

<span data-ttu-id="20f6e-122">Eine benutzerdefinierte Registerkarte wird im App-Manifest des App-Pakets deklariert.</span><span class="sxs-lookup"><span data-stu-id="20f6e-122">A custom tab is declared in the app manifest of your app package.</span></span> <span data-ttu-id="20f6e-123">Für jede Webseite, die als Registerkarte in Ihrer APP enthalten sein soll, definieren Sie eine URL und einen Bereich.</span><span class="sxs-lookup"><span data-stu-id="20f6e-123">For each webpage you want included as a tab in your app you define a URL and a scope.</span></span> <span data-ttu-id="20f6e-124">Darüber hinaus müssen Sie das Microsoft [Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client) zu Ihrer Seite hinzu `microsoftTeams.initialize()` fügen und nach dem Laden der Seite anrufen.</span><span class="sxs-lookup"><span data-stu-id="20f6e-124">Additionally, you need to add the [Teams JavaScript client SDK](/javascript/api/overview/msteams-client) to your page, and call `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="20f6e-125">Dadurch wird Microsoft Teams mitgeteilt, dass Sie Ihre Seite anzeigen, Ihnen Zugriff auf Teams-spezifische Informationen ermöglichen (beispielsweise, wenn der Team-Client das dunkle Design ausführt) und Ihnen die Möglichkeit geben, basierend auf den Ergebnissen Maßnahmen zu ergreifen.</span><span class="sxs-lookup"><span data-stu-id="20f6e-125">Doing so will tell Teams to display your page, give you access to Teams-specific information (for example if the Teams client is running the Dark Theme), and allow you to take action based on the results.</span></span>

<span data-ttu-id="20f6e-126">Unabhängig davon, ob Sie die Registerkarte innerhalb des Kanals/der Gruppe oder des persönlichen Bereichs verfügbar machen möchten, müssen Sie auf Ihrer Registerkarte eine iframed HTML- [Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md) präsentieren. Bei persönlichen Registerkarten wird die Inhalts-URL direkt in ihrem Manifest durch die `contentUrl` -Eigenschaft im `staticTabs` Array festgelegt.</span><span class="sxs-lookup"><span data-stu-id="20f6e-126">Whether you choose to expose your tab within the channel/group or personal scope, you'll need to present an IFramed HTML [content page](~/tabs/how-to/create-tab-pages/content-page.md) in your tab. For personal tabs, the content URL is set directly in your manifest by the `contentUrl` property in the `staticTabs` array.</span></span> <span data-ttu-id="20f6e-127">Die Inhalte Ihrer Registerkarte sind für alle Benutzer gleich.</span><span class="sxs-lookup"><span data-stu-id="20f6e-127">Your tab's content will be the same for all users.</span></span>

<span data-ttu-id="20f6e-128">Für Channel/Group-Registerkarten müssen Sie auch eine zusätzliche Konfigurationsseite erstellen, mit der Ihre Benutzer ihre Inhaltsseiten-URL konfigurieren können, normalerweise mithilfe von URL-Abfragezeichenfolgenparametern, um den entsprechenden Inhalt für diesen Kontext zu laden.</span><span class="sxs-lookup"><span data-stu-id="20f6e-128">For channel/group tabs, you also need to create an additional configuration page that allows your users to configure your content page URL, typically by using URL query string parameters to load the appropriate content for that context.</span></span> <span data-ttu-id="20f6e-129">Dies liegt daran, dass die Registerkarte Kanal/Gruppe mehreren verschiedenen Teams oder Gruppenchats hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="20f6e-129">This is because your channel/group tab can be added to multiple different teams or group chats.</span></span> <span data-ttu-id="20f6e-130">Bei jeder nachfolgenden Installation können die Benutzer die Registerkarte so konfigurieren, dass Sie die Umgebung nach Bedarf anpassen können.</span><span class="sxs-lookup"><span data-stu-id="20f6e-130">On each subsequent install, your users will be able to configure the tab allowing you to tailor the experience as needed.</span></span> <span data-ttu-id="20f6e-131">Wenn Sie beispielsweise die Registerkarte Azure DevOps Board hinzufügen, können Sie auf der Konfigurationsseite auswählen, welches Board die Registerkarte laden soll.</span><span class="sxs-lookup"><span data-stu-id="20f6e-131">For example, when you add the Azure DevOps board tab the configuration page allows you to choose which board the tab will load.</span></span> <span data-ttu-id="20f6e-132">Die URL der Konfigurationsseite wird durch die `configurationUrl` -Eigenschaft im `configurableTabs` Array in Ihrem App-Manifest angegeben.</span><span class="sxs-lookup"><span data-stu-id="20f6e-132">The configuration page URL is specified by the  `configurationUrl` property in the `configurableTabs` array in your app manifest.</span></span>

<span data-ttu-id="20f6e-133">Sie können maximal eine (1) Kanal/Gruppen-Registerkarte und bis zu sechzehn (16) persönliche Registerkarten pro APP haben.</span><span class="sxs-lookup"><span data-stu-id="20f6e-133">You can have a maximum of one (1) channel/group tab and up to sixteen (16) personal tabs per app.</span></span>

## <a name="mobile-clients"></a><span data-ttu-id="20f6e-134">Mobile Clients</span><span class="sxs-lookup"><span data-stu-id="20f6e-134">Mobile clients</span></span>

<span data-ttu-id="20f6e-135">Wenn die Registerkarte Kanal/Gruppe auf mobilen Teams-Clients angezeigt werden soll, muss `setSettings()` die Konfiguration über einen Wert für die `websiteUrl` Eigenschaft verfügen (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="20f6e-135">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span> <span data-ttu-id="20f6e-136">Persönliche Registerkarten sind derzeit in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="20f6e-136">Personal tabs are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span> <span data-ttu-id="20f6e-137">Die vollständige Unterstützung für Registerkarten auf mobilen Clients wird in Kürze veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="20f6e-137">Full support for tabs on mobile clients will be released soon.</span></span> <span data-ttu-id="20f6e-138">Zur Vorbereitung des Updates sollten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten befolgten.</span><span class="sxs-lookup"><span data-stu-id="20f6e-138">To prepare for the update, you should follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span>