---
title: Nach Veröffentlichung
description: Vorgehensweisen nach dem Veröffentlichen der APP
keywords: Update-App-Update-Manifest für Teams nach Veröffentlichungs Update Zertifizierung
ms.openlocfilehash: 58e81688ab9a8b55d2b035fc9b43cb58dddb6133
ms.sourcegitcommit: 25afe104d10c9a6a2849decf5ec1d08969d827c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "48465915"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="e4036-104">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="e4036-104">Maintain and support your published app</span></span> 

<span data-ttu-id="e4036-105">Nachdem Ihre APP genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erweitern, indem Sie das Microsoft 365 App Compliance-Programm ausfüllen oder eine Download Schaltfläche auf Ihrer Website hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e4036-105">After your app is approved and listed in the public app catalog, you can increase your reach by completing the Microsoft 365 App Compliance Program or by adding a download button on your website.</span></span>

## <a name="microsoft-365-certified"></a><span data-ttu-id="e4036-106">Microsoft 365 zertifiziert</span><span class="sxs-lookup"><span data-stu-id="e4036-106">Microsoft 365 Certified</span></span>

<span data-ttu-id="e4036-107">Das [Microsoft 365 App Compliance-Programm](./application-certification.md)ist ein dreistufiger Ansatz für App-Sicherheit und-Compliance.</span><span class="sxs-lookup"><span data-stu-id="e4036-107">The [Microsoft 365 App Compliance Program](./application-certification.md), is a three tier approach to app security and compliance.</span></span> <span data-ttu-id="e4036-108">Jede Schicht baut auf dem nächsten auf – bietet ein mehrstufiges Programm, um die Anforderungen Ihrer Kunden zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="e4036-108">Each tier builds upon the next – offering a layered program to meet your customer’s needs.</span></span> <span data-ttu-id="e4036-109">Weitere Informationen zur Sicherheit und Compliance-Haltung von Teams-apps finden Sie auf der [Seite "Kompatibilität"](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span><span class="sxs-lookup"><span data-stu-id="e4036-109">You can learn more about the security and compliance posture of Teams apps by visiting the [compliance page](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="e4036-110">Hinzufügen einer Schaltfläche zum herunterladen zu ihrer Produkt Website</span><span class="sxs-lookup"><span data-stu-id="e4036-110">Add a download button to your product site</span></span>

<span data-ttu-id="e4036-111">Wenn Ihre APP im Microsoft Teams Global Store installiert ist, können Sie einen Link für Ihre Website generieren, der Teams startet und eine Zustimmung und ein Installationsdialogfeld für Benutzer zur Verfügung stellt, um die APP hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e4036-111">If your app is in the Microsoft Teams global store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="e4036-112">Das Format lautet:  `https://teams.microsoft.com/l/app/<appId>` wobei die ID die GUID ist, die Sie im übermittelten Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="e4036-112">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="e4036-113">Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.</span><span class="sxs-lookup"><span data-stu-id="e4036-113">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="e4036-114">Aktualisieren der vorhandenen Teams-App</span><span class="sxs-lookup"><span data-stu-id="e4036-114">Updating your existing Teams app</span></span>

* <span data-ttu-id="e4036-115">Verwenden Sie nicht die Schaltfläche *neue APP hinzufügen* , um Ihre APP erneut zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="e4036-115">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="e4036-116">Verwenden Sie stattdessen die Kachel für Ihre APP auf der Registerkarte Übersicht.</span><span class="sxs-lookup"><span data-stu-id="e4036-116">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="e4036-117">Die im aktualisierten Manifest enthaltene-ID sollte mit einer erhöhten Versionsnummer im aktuellen Manifest identisch sein.</span><span class="sxs-lookup"><span data-stu-id="e4036-117">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="e4036-118">Erhöhen Sie die Versionsnummer im Manifest, wenn Sie Änderungen an ihrer Übermittlung einschließlich des App-namens oder aller Metadaten im Manifest vornehmen.</span><span class="sxs-lookup"><span data-stu-id="e4036-118">Increment your version number in the manifest if you make any changes to your submission including app name or any metadata in the manifest.</span></span>
* <span data-ttu-id="e4036-119">Aktualisierte Übermittlungen sind erforderlich, um einem neuen Überprüfungs-und Validierungsprozess unterzogen zu werden.</span><span class="sxs-lookup"><span data-stu-id="e4036-119">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="e4036-120">APP-Updates und der Benutzer Zustimmungs Fluss</span><span class="sxs-lookup"><span data-stu-id="e4036-120">App updates and the user consent flow</span></span>

<span data-ttu-id="e4036-121">Wenn ein Benutzer Ihre Anwendung installiert eines der ersten Schritte, die Sie ausführen, ist die Zustimmung, der APP die Berechtigung für den Zugriff auf die Dienste und Informationen zu erteilen, die die APP für Ihre Aufgabe benötigt.</span><span class="sxs-lookup"><span data-stu-id="e4036-121">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="e4036-122">In den meisten Fällen wird, nachdem Sie ein App-Update abgeschlossen haben, die neue Version automatisch für Endbenutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e4036-122">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="e4036-123">Es gibt jedoch einige Updates für das [Teams-App-Manifest](../../../../resources/schema/manifest-schema.md) , die eine Benutzerakzeptanz erfordern und das Zustimmungs Verhalten erneut auslösen können:</span><span class="sxs-lookup"><span data-stu-id="e4036-123">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="e4036-124">Ein bot wurde hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="e4036-124">A bot was added or removed.</span></span>
> * <span data-ttu-id="e4036-125">Der eindeutige Wert eines vorhandenen bot `botId` wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="e4036-125">An existing bot's unique `botId` value changed.</span></span>
> * <span data-ttu-id="e4036-126">Der boolesche Wert eines vorhandenen bot `isNotificationOnly` wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="e4036-126">An existing bot's `isNotificationOnly` boolean value changed.</span></span>
> * <span data-ttu-id="e4036-127">Der boolesche Wert eines vorhandenen bot `supportsFiles` wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="e4036-127">An existing bot's `supportsFiles` boolean value changed.</span></span>
> * <span data-ttu-id="e4036-128">Eine Messaging Erweiterung ( `composeExtensions` ) wurde hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="e4036-128">A messaging extension (`composeExtensions`) was added or removed.</span></span>
> * <span data-ttu-id="e4036-129">Ein neuer Connector wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e4036-129">A new connector was added.</span></span>
> * <span data-ttu-id="e4036-130">Eine neue Registerkarte statisch/persönlich wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e4036-130">A new static/personal tab was added.</span></span>
> * <span data-ttu-id="e4036-131">Es wurde eine neue konfigurierbare Gruppe/Kanal-Registerkarte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e4036-131">A new configurable group/channel tab was added.</span></span>
> * <span data-ttu-id="e4036-132">Die `webApplicationInfo` Werte wurden geändert.</span><span class="sxs-lookup"><span data-stu-id="e4036-132">The `webApplicationInfo` values changed.</span></span>
>
