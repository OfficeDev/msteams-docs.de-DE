---
title: Voraussetzungen
author: surbhigupta
description: Jede Registerkarte in Microsoft Teams muss diese Anforderungen erfüllen.
keywords: Konfigurierbarer Gruppenkanal für Teams-Registerkarten
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 8566bb0457db76e4639593dcd67a0442749c0a31
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179937"
---
# <a name="prerequisites"></a><span data-ttu-id="91285-104">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="91285-104">Prerequisites</span></span>

<span data-ttu-id="91285-105">Teams Registerkarten müssen die folgenden Voraussetzungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="91285-105">Teams tabs must adhere to the following prerequisites:</span></span>

* <span data-ttu-id="91285-106">Sie müssen zulassen, dass Ihre Registerkartenseiten in einem iFrame angezeigt werden, indem Sie X-Frame-Optionen und HTTP-Antwortheader für Inhaltssicherheitsrichtlinien verwenden.</span><span class="sxs-lookup"><span data-stu-id="91285-106">You must allow your tab pages to be shown in an iFrame, using X-Frame-Options and Content-Security-Policy HTTP response headers.</span></span>
  * <span data-ttu-id="91285-107">Header festlegen: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span><span class="sxs-lookup"><span data-stu-id="91285-107">Set header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`</span></span>
  * <span data-ttu-id="91285-108">Legen Sie aus Gründen der Internet Explorer 11-Kompatibilität `X-Content-Security-Policy` fest.</span><span class="sxs-lookup"><span data-stu-id="91285-108">For Internet Explorer 11 compatibility, set `X-Content-Security-Policy`.</span></span>
  * <span data-ttu-id="91285-109">Legen Sie alternativ die Kopfzeile `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/` fest.</span><span class="sxs-lookup"><span data-stu-id="91285-109">Alternately, set header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`.</span></span> <span data-ttu-id="91285-110">Dieser Header ist veraltet, wird aber von den meisten Browsern weiterhin akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="91285-110">This header is deprecated but still accepted by most browsers.</span></span>

* <span data-ttu-id="91285-111">Als Schutz vor Clickjacking werden Anmeldeseiten in der Regel nicht in iFrames gerendert.</span><span class="sxs-lookup"><span data-stu-id="91285-111">Typically, as a safeguard against clickjacking, login pages do not render in iFrames.</span></span> <span data-ttu-id="91285-112">Ihre Authentifizierungslogik muss eine andere Methode als die Umleitung verwenden.</span><span class="sxs-lookup"><span data-stu-id="91285-112">Your authentication logic needs to use a method other than redirect.</span></span> <span data-ttu-id="91285-113">Verwenden Sie beispielsweise die token- oder cookiebasierte Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="91285-113">For example, use token-based or cookie-based authentication.</span></span>

    > [!NOTE]
    > <span data-ttu-id="91285-114">Chrome 80, das Anfang 2020 veröffentlicht werden soll, führt neue Cookiewerte ein und erlegt standardmäßig Cookierichtlinien auf.</span><span class="sxs-lookup"><span data-stu-id="91285-114">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="91285-115">Es wird empfohlen, die beabsichtigte Verwendung für Ihre Cookies festzulegen, anstatt sich auf das Standardverhalten des Browsers zu verlassen.</span><span class="sxs-lookup"><span data-stu-id="91285-115">It is recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="91285-116">Weitere Informationen finden Sie unter [SameSite-Cookieattribut.](../../resources/samesite-cookie-update.md)</span><span class="sxs-lookup"><span data-stu-id="91285-116">For more information, see [SameSite cookie attribute](../../resources/samesite-cookie-update.md).</span></span>

* <span data-ttu-id="91285-117">Browser halten sich an eine Einschränkung der Richtlinie für den gleichen Ursprung.</span><span class="sxs-lookup"><span data-stu-id="91285-117">Browsers adhere to a same-origin policy restriction.</span></span> <span data-ttu-id="91285-118">Es verhindert, dass Webseiten Anforderungen an andere Domänen als die bereitgestellte Webseite senden.</span><span class="sxs-lookup"><span data-stu-id="91285-118">It prevents webpages from making requests to different domains than the served web page.</span></span> <span data-ttu-id="91285-119">Sie können die Konfigurations- oder Inhaltsseite jedoch an eine andere Domäne oder Unterdomäne umleiten.</span><span class="sxs-lookup"><span data-stu-id="91285-119">However, you can redirect the configuration or content page to another domain or subdomain.</span></span> <span data-ttu-id="91285-120">Ihre domänenübergreifende Navigationslogik muss es dem Teams-Client ermöglichen, den Ursprung anhand einer statischen `validDomains` Liste im App-Manifest beim Laden oder Kommunizieren mit der Registerkarte zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="91285-120">Your cross-domain navigation logic must allow the Teams client to validate the origin against a static `validDomains` list in the app manifest when loading or communicating with the tab.</span></span>

* <span data-ttu-id="91285-121">Sie müssen ihre Registerkarten basierend auf dem Design, dem Design und der Absicht des Teams Clients formatieren.</span><span class="sxs-lookup"><span data-stu-id="91285-121">You must style your tabs based on the Teams client's theme, design, and intent.</span></span> <span data-ttu-id="91285-122">Registerkarten funktionieren in der Regel am besten, wenn sie so erstellt werden, dass sie einem bestimmten Bedarf entsprechen und sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge von Daten konzentrieren, die für den Kanalspeicherort der Registerkarte relevant sind.</span><span class="sxs-lookup"><span data-stu-id="91285-122">Typically, tabs work best when they are built to address a specific need and focus on a small set of tasks or a subset of data that is relevant to the tab's channel location.</span></span>

* <span data-ttu-id="91285-123">Fügen Sie innerhalb Ihrer Inhaltsseite einen Verweis auf [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) mithilfe von Skripttags hinzu.</span><span class="sxs-lookup"><span data-stu-id="91285-123">Within your content page, add a reference to [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) using script tags.</span></span> <span data-ttu-id="91285-124">Nachdem die Seite geladen wurde, rufen Sie sie `microsoftTeams.initialize()` auf, andernfalls wird die Seite nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91285-124">After your page loads, make a call to `microsoftTeams.initialize()`, otherwise your page is not displayed.</span></span>

* <span data-ttu-id="91285-125">Damit die Authentifizierung auf mobilen Clients funktioniert, müssen Sie Teams JavaScript SDK auf mindestens Version 1.4.1 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="91285-125">For authentication to work on mobile clients, you must upgrade Teams JavaScript SDK to at least version 1.4.1.</span></span>

* <span data-ttu-id="91285-126">Wenn Ihre Kanal- oder Gruppenregisterkarte auf Teams mobilen Clients angezeigt werden soll, muss die `setSettings()` Konfiguration einen Wert für die Eigenschaft `websiteUrl` aufweisen.</span><span class="sxs-lookup"><span data-stu-id="91285-126">If you choose to have your channel or group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.</span></span>

* <span data-ttu-id="91285-127">Die Registerkarte "MS Teams" unterstützt nicht die Möglichkeit, Intranetwebsites zu laden, die selbstsignte Zertifikate verwenden.</span><span class="sxs-lookup"><span data-stu-id="91285-127">MS Teams tab does not support the ability to load intranet websites that use self-signed certificates.</span></span>

## <a name="see-also"></a><span data-ttu-id="91285-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="91285-128">See also</span></span>

* [<span data-ttu-id="91285-129">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="91285-129">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="91285-130">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="91285-130">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="91285-131">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="91285-131">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)

## <a name="next-step"></a><span data-ttu-id="91285-132">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="91285-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="91285-133">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="91285-133">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
