---
title: Nach Veröffentlichung
description: Vorgehensweisen nach dem Veröffentlichen der APP
keywords: Update Zertifikat für Teams nach Veröffentlichung
ms.openlocfilehash: 77b74d77546de0ae93b0ae39aec925d2e3dec2cf
ms.sourcegitcommit: fdc50183f3f4bec9e4b83bcfe5e016b591402f7c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "44867094"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="6e9a0-104">Verwalten und unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="6e9a0-104">Maintain and support your published app</span></span> 

<span data-ttu-id="6e9a0-105">Nachdem Ihre APP genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erweitern, indem Sie die APP-Zertifizierung erreichen oder eine Download Schaltfläche Ihrer Website hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-105">After your app is approved and listed in the public app catalog, you can increase your reach by achieving app certification, or adding a download button your website.</span></span>

## <a name="application-certificate"></a><span data-ttu-id="6e9a0-106">Anwendungszertifikat</span><span class="sxs-lookup"><span data-stu-id="6e9a0-106">Application Certificate</span></span>

<span data-ttu-id="6e9a0-107">Microsoft stellt ein [Anwendungs Zertifizierungsprogramm](./application-certification.md) bereit, das Ihre APP-Informationen kompiliert und auf der [Seite Microsoft Teams-App-Sicherheit und-Kompatibilität](https://aka.ms/AppCertification)präsentiert.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-107">Microsoft provides a [Application Certification program](./application-certification.md) that compiles your app information and presents it on [Microsoft Teams App Security and Compliance Page](https://aka.ms/AppCertification).</span></span> <span data-ttu-id="6e9a0-108">Diese Informationen sollen Administratoren dabei helfen, Apps auszuwählen, die für Ihre Organisation sicher sind.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-108">This information is intended to help admins to choose apps that are safe for their organizations.</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="6e9a0-109">Hinzufügen einer Schaltfläche zum herunterladen zu ihrer Produkt Website</span><span class="sxs-lookup"><span data-stu-id="6e9a0-109">Add a download button to your product site</span></span>

<span data-ttu-id="6e9a0-110">Wenn Ihre APP im Microsoft Teams Store gespeichert ist, können Sie einen Link für Ihre Website generieren, der Teams startet und eine Zustimmung und ein Installationsdialogfeld für Benutzer zum Hinzufügen der APP anzeigt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-110">If your app is in the Microsoft Teams store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="6e9a0-111">Das Format lautet: `https://teams.microsoft.com/l/app/<appId>` wobei die ID die GUID ist, die Sie im übermittelten Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-111">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="6e9a0-112">Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-112">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="6e9a0-113">Aktualisieren der vorhandenen Teams-App</span><span class="sxs-lookup"><span data-stu-id="6e9a0-113">Updating your existing Teams app</span></span>

* <span data-ttu-id="6e9a0-114">Verwenden Sie nicht die Schaltfläche *neue APP hinzufügen* , um Ihre APP erneut zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-114">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="6e9a0-115">Verwenden Sie stattdessen die Kachel für Ihre APP auf der Registerkarte Übersicht.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-115">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="6e9a0-116">Die im aktualisierten Manifest enthaltene-ID sollte mit einer erhöhten Versionsnummer im aktuellen Manifest identisch sein.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-116">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="6e9a0-117">Erhöhen Sie die Versionsnummer im Manifest, wenn Sie Änderungen an ihrer Übermittlung an den Manifesten vornehmen.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-117">Increment your version number in the manifest if you make any manifest changes to your submission.</span></span>
* <span data-ttu-id="6e9a0-118">Aktualisierte Übermittlungen sind erforderlich, um einem neuen Überprüfungs-und Validierungsprozess unterzogen zu werden.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-118">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="6e9a0-119">APP-Updates und der Benutzer Zustimmungs Fluss</span><span class="sxs-lookup"><span data-stu-id="6e9a0-119">App updates and the user consent flow</span></span>

<span data-ttu-id="6e9a0-120">Wenn ein Benutzer Ihre Anwendung installiert eines der ersten Schritte, die Sie ausführen, ist die Zustimmung, der APP die Berechtigung für den Zugriff auf die Dienste und Informationen zu erteilen, die die APP für Ihre Aufgabe benötigt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-120">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="6e9a0-121">In den meisten Fällen wird, nachdem Sie ein App-Update abgeschlossen haben, die neue Version automatisch für Endbenutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-121">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="6e9a0-122">Es gibt jedoch einige Updates für das [Teams-App-Manifest](../../../../resources/schema/manifest-schema.md) , die eine Benutzerakzeptanz erfordern und das Zustimmungs Verhalten erneut auslösen können:</span><span class="sxs-lookup"><span data-stu-id="6e9a0-122">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="6e9a0-123">Ein bot wurde hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-123">A bot was added or removed.</span></span>
> * <span data-ttu-id="6e9a0-124">Der eindeutige Wert eines vorhandenen bot `botId` wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-124">An existing bot's unique `botId` value changed.</span></span>
> * <span data-ttu-id="6e9a0-125">Der boolesche Wert eines vorhandenen bot `isNotificationOnly` wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-125">An existing bot's `isNotificationOnly` boolean value changed.</span></span>
> * <span data-ttu-id="6e9a0-126">Der boolesche Wert eines vorhandenen bot `supportsFiles` wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-126">An existing bot's `supportsFiles` boolean value changed.</span></span>
> * <span data-ttu-id="6e9a0-127">Eine Messaging Erweiterung ( `composeExtensions` ) wurde hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-127">A messaging extension (`composeExtensions`) was added or removed.</span></span>
> * <span data-ttu-id="6e9a0-128">Ein neuer Connector wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-128">A new connector was added.</span></span>
> * <span data-ttu-id="6e9a0-129">Eine neue Registerkarte statisch/persönlich wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-129">A new static/personal tab was added.</span></span>
> * <span data-ttu-id="6e9a0-130">Es wurde eine neue konfigurierbare Gruppe/Kanal-Registerkarte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-130">A new configurable group/channel tab was added.</span></span>
> * <span data-ttu-id="6e9a0-131">Die `webApplicationInfo` Werte wurden geändert.</span><span class="sxs-lookup"><span data-stu-id="6e9a0-131">The `webApplicationInfo` values changed.</span></span>
>