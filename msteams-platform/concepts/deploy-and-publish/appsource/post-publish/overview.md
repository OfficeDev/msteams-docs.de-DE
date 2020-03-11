---
title: Nach Veröffentlichung
description: Vorgehensweisen nach dem Veröffentlichen der APP
keywords: Update Zertifikat für Teams nach Veröffentlichung
ms.openlocfilehash: 54d0615c262e45729a36f556c3eda3b810d2a097
ms.sourcegitcommit: 2a84a3c8b10771e37ce51bf603a967633947a3e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "42582860"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="71484-104">Verwalten und unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="71484-104">Maintain and support your published app</span></span> 

<span data-ttu-id="71484-105">Nachdem Ihre APP genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erweitern, indem Sie die APP-Zertifizierung erreichen oder eine Download Schaltfläche Ihrer Website hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="71484-105">After your app is approved and listed in the public app catalog, you can increase your reach by achieving app certification, or adding a download button your website.</span></span>

## <a name="application-certificate"></a><span data-ttu-id="71484-106">Anwendungszertifikat</span><span class="sxs-lookup"><span data-stu-id="71484-106">Application Certificate</span></span>

<span data-ttu-id="71484-107">Microsoft stellt ein [Anwendungs Zertifizierungsprogramm](./application-certification.md) bereit, das Ihre APP-Informationen kompiliert und auf der [Seite Microsoft Teams-App-Sicherheit und-Kompatibilität](https://aka.ms/AppCertification)präsentiert.</span><span class="sxs-lookup"><span data-stu-id="71484-107">Microsoft provides a [Application Certification program](./application-certification.md) that compiles your app information and presents it on [Microsoft Teams App Security and Compliance Page](https://aka.ms/AppCertification).</span></span> <span data-ttu-id="71484-108">Diese Informationen sollen Administratoren dabei helfen, Apps auszuwählen, die für Ihre Organisation sicher sind.</span><span class="sxs-lookup"><span data-stu-id="71484-108">This information is intended to help admins to choose apps that are safe for their organizations.</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="71484-109">Hinzufügen einer Schaltfläche zum herunterladen zu ihrer Produkt Website</span><span class="sxs-lookup"><span data-stu-id="71484-109">Add a download button to your product site</span></span>

<span data-ttu-id="71484-110">Wenn Ihre APP im Microsoft Teams Store gespeichert ist, können Sie einen Link für Ihre Website generieren, der Teams startet und eine Zustimmung und ein Installationsdialogfeld für Benutzer zum Hinzufügen der APP anzeigt.</span><span class="sxs-lookup"><span data-stu-id="71484-110">If your app is in the Microsoft Teams store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="71484-111">Das Format lautet: `https://teams.microsoft.com/l/app/<appId>` wobei die ID die GUID ist, die Sie im übermittelten Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="71484-111">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="71484-112">Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.</span><span class="sxs-lookup"><span data-stu-id="71484-112">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="71484-113">Aktualisieren der vorhandenen Teams-App</span><span class="sxs-lookup"><span data-stu-id="71484-113">Updating your existing Teams app</span></span>

* <span data-ttu-id="71484-114">Verwenden Sie nicht die Schaltfläche *neue APP hinzufügen* , um Ihre APP erneut zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="71484-114">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="71484-115">Verwenden Sie stattdessen die Kachel für Ihre APP auf der Registerkarte Übersicht.</span><span class="sxs-lookup"><span data-stu-id="71484-115">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="71484-116">Die im aktualisierten Manifest enthaltene-ID sollte mit einer erhöhten Versionsnummer im aktuellen Manifest identisch sein.</span><span class="sxs-lookup"><span data-stu-id="71484-116">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="71484-117">Erhöhen Sie die Versionsnummer im Manifest, wenn Sie Änderungen an ihrer Übermittlung an den Manifesten vornehmen.</span><span class="sxs-lookup"><span data-stu-id="71484-117">Increment your version number in the manifest if you make any manifest changes to your submission.</span></span>
* <span data-ttu-id="71484-118">Aktualisierte Übermittlungen sind erforderlich, um einem neuen Überprüfungs-und Validierungsprozess unterzogen zu werden.</span><span class="sxs-lookup"><span data-stu-id="71484-118">Updated submissions are required to undergo a new review and validation process.</span></span>


### <a name="when-does-updating-your-app-trigger-the-user-consent-flow"></a><span data-ttu-id="71484-119">Wann löst die Aktualisierung Ihrer APP den Benutzer Zustimmungs Fluss aus?</span><span class="sxs-lookup"><span data-stu-id="71484-119">When does updating your app trigger the user consent flow?</span></span>

<span data-ttu-id="71484-120">Wenn ein Benutzer Ihre Anwendung installiert eines der ersten Schritte, die Sie ausführen, ist die Zustimmung, der APP die Berechtigung für den Zugriff auf die Dienste und Informationen zu erteilen, die die APP für Ihre Aufgabe benötigt.</span><span class="sxs-lookup"><span data-stu-id="71484-120">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="71484-121">Wenn Sie Ihre APP aktualisieren, kann dies das Zustimmungs Verhalten erneut auslösen, insbesondere dann, wenn Sie eine oder mehrere der folgenden Änderungen vorgenommen haben:</span><span class="sxs-lookup"><span data-stu-id="71484-121">When you update your app, that can re-trigger this consent behavior, particularly if you have made one or more of the following changes:</span></span>

* <span data-ttu-id="71484-122">Hinzufügen einer neuen Funktion zu einer APP, beispielsweise Hinzufügen eines bot zu einer nur-Tab-app.</span><span class="sxs-lookup"><span data-stu-id="71484-122">Adding a new capability to an app such as adding a bot to an tab only app.</span></span>
* <span data-ttu-id="71484-123">Ändern des Berechtigungs Arrays im Manifest.</span><span class="sxs-lookup"><span data-stu-id="71484-123">Changing the permissions array in the manifest.</span></span>
* <span data-ttu-id="71484-124">Inkrementieren der APP-Versionsnummer in ihrem Manifest.</span><span class="sxs-lookup"><span data-stu-id="71484-124">Incrementing your app version number in your manifest.</span></span>
