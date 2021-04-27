---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Was tun, nachdem Sie Ihre App veröffentlicht haben
ms.topic: how-to
localization_priority: Normal
keywords: Updateupdateupdateupdatemanifest für Teams nach der Veröffentlichung
ms.openlocfilehash: 11c32ce61664f34a246905124b767e17d3c6f536
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020800"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="07384-104">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="07384-104">Maintain and support your published app</span></span> 

<span data-ttu-id="07384-105">Nachdem Ihre App genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erhöhen, indem Sie das Microsoft 365 App Compliance Program abschließen oder eine Downloadschaltfläche auf Ihrer Website hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="07384-105">After your app is approved and listed in the public app catalog, you can increase your reach by completing the Microsoft 365 App Compliance Program or by adding a download button on your website.</span></span>

## <a name="microsoft-365-certified"></a><span data-ttu-id="07384-106">Microsoft 365 Certified</span><span class="sxs-lookup"><span data-stu-id="07384-106">Microsoft 365 Certified</span></span>

<span data-ttu-id="07384-107">Das [Microsoft 365 App Compliance Program](./application-certification.md)ist ein dreistufiger Ansatz für die Sicherheit und Compliance von Apps.</span><span class="sxs-lookup"><span data-stu-id="07384-107">The [Microsoft 365 App Compliance Program](./application-certification.md), is a three tier approach to app security and compliance.</span></span> <span data-ttu-id="07384-108">Jede Ebene baut auf der nächsten auf – und bietet ein mehrschichtiges Programm, das den Anforderungen Ihres Kunden entspricht.</span><span class="sxs-lookup"><span data-stu-id="07384-108">Each tier builds upon the next – offering a layered program to meet your customer’s needs.</span></span> <span data-ttu-id="07384-109">Weitere Informationen zur Sicherheits- und Compliancehaltung von Teams-Apps finden Sie auf der Seite ["Compliance".](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps)</span><span class="sxs-lookup"><span data-stu-id="07384-109">You can learn more about the security and compliance posture of Teams apps by visiting the [compliance page](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="07384-110">Hinzufügen einer Downloadschaltfläche zu Ihrer Produktwebsite</span><span class="sxs-lookup"><span data-stu-id="07384-110">Add a download button to your product site</span></span>

<span data-ttu-id="07384-111">Wenn Sich Ihre App im globalen Microsoft Teams Store befindet, können Sie einen Link für Ihre Website generieren, der Teams startet und ein Zustimmungs- und Installationsdialogfeld für Benutzer zum Hinzufügen der App zeigt.</span><span class="sxs-lookup"><span data-stu-id="07384-111">If your app is in the Microsoft Teams global store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="07384-112">Das Format ist:  `https://teams.microsoft.com/l/app/<appId>` dabei ist appID die GUID, die sie im übermittelten Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="07384-112">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="07384-113">Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` ist der Link zum Installieren von Trello.</span><span class="sxs-lookup"><span data-stu-id="07384-113">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="07384-114">Aktualisieren Ihrer vorhandenen Teams-App</span><span class="sxs-lookup"><span data-stu-id="07384-114">Updating your existing Teams app</span></span>

* <span data-ttu-id="07384-115">Verwenden Sie nicht die *Schaltfläche Neue App hinzufügen,* um Ihre App erneut zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="07384-115">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="07384-116">Verwenden Sie stattdessen die Kachel für Ihre App auf der Registerkarte Übersicht.</span><span class="sxs-lookup"><span data-stu-id="07384-116">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="07384-117">Die appId im aktualisierten Manifest sollte mit der im aktuellen Manifest identisch sein, mit einer inkrementierten Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="07384-117">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="07384-118">Erhöhen Sie Ihre Versionsnummer im Manifest, wenn Sie Änderungen an Ihrer Übermittlung vornehmen, einschließlich des App-Namens oder metadaten im Manifest.</span><span class="sxs-lookup"><span data-stu-id="07384-118">Increment your version number in the manifest if you make any changes to your submission including app name or any metadata in the manifest.</span></span>
* <span data-ttu-id="07384-119">Aktualisierte Übermittlungen sind erforderlich, um einen neuen Überprüfungs- und Überprüfungsprozess durchlaufen zu können.</span><span class="sxs-lookup"><span data-stu-id="07384-119">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="07384-120">App-Updates und der Benutzer-Zustimmungsfluss</span><span class="sxs-lookup"><span data-stu-id="07384-120">App updates and the user consent flow</span></span>

<span data-ttu-id="07384-121">Wenn ein Benutzer Ihre Anwendung installiert, ist eine der ersten Aufgaben die Zustimmung, der App die Berechtigung zum Zugriff auf die Dienste und Informationen zu erteilen, die die App benötigt, um ihre Aufgabe zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="07384-121">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="07384-122">In den meisten Fällen wird die neue Version nach Abschluss eines App-Updates automatisch für Endbenutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="07384-122">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="07384-123">Es gibt jedoch einige Updates für das [Teams-App-Manifest,](../../../../resources/schema/manifest-schema.md) für die die Benutzerakzeptanz erforderlich ist und dieses Zustimmungsverhalten erneut auslösen kann:</span><span class="sxs-lookup"><span data-stu-id="07384-123">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="07384-124">Ein Bot wird hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="07384-124">A bot is added or removed.</span></span>
> * <span data-ttu-id="07384-125">Der eindeutige Wert eines vorhandenen `botId` Bots wird geändert.</span><span class="sxs-lookup"><span data-stu-id="07384-125">An existing bot's unique `botId` value is changed.</span></span>
> * <span data-ttu-id="07384-126">Der boolesche Wert eines `isNotificationOnly` vorhandenen Bots wird geändert.</span><span class="sxs-lookup"><span data-stu-id="07384-126">An existing bot's `isNotificationOnly` boolean value is changed.</span></span>
> * <span data-ttu-id="07384-127">Der oder der boolesche Wert eines vorhandenen `supportsFiles` `supportsCalling` Bots wird geändert.</span><span class="sxs-lookup"><span data-stu-id="07384-127">An existing bot's `supportsFiles` or `supportsCalling` boolean value is changed.</span></span>
> * <span data-ttu-id="07384-128">Eine Messagingerweiterung `composeExtensions` wird hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="07384-128">A messaging extension `composeExtensions` is added or removed.</span></span>
> * <span data-ttu-id="07384-129">Es wird ein neuer Connector hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="07384-129">A new connector is added.</span></span>
> * <span data-ttu-id="07384-130">Eine neue statische oder persönliche Registerkarte wird hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="07384-130">A new static or personal tab is added.</span></span>
> * <span data-ttu-id="07384-131">Eine neue konfigurierbare Gruppe oder Kanalregisterkarte wird hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="07384-131">A new configurable group or channel tab is added.</span></span>
> * <span data-ttu-id="07384-132">Die Darin enthaltenen `webApplicationInfo` Eigenschaften werden geändert.</span><span class="sxs-lookup"><span data-stu-id="07384-132">The properties inside `webApplicationInfo` are changed.</span></span> <span data-ttu-id="07384-133">Für Änderungen `webApplicationInfo` an ist die Zustimmung nur im Bereich Teams erforderlich.</span><span class="sxs-lookup"><span data-stu-id="07384-133">For changes to `webApplicationInfo`, consent is only required in the Teams scope.</span></span>

### <a name="images-of-user-consent-flow"></a><span data-ttu-id="07384-134">Bilder des Benutzer-Zustimmungsflusses:</span><span class="sxs-lookup"><span data-stu-id="07384-134">Images of user consent flow:</span></span>

<span data-ttu-id="07384-135">**Einrichten eines Connectors** – Dieser Bildschirm wird nur für Teams-Benutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="07384-135">**Set up a connector** —  This screen will appear only for Teams users.</span></span>

![Einrichten eines Konnektordiagramms für den Zustimmungsfluss](../../../../assets/images/connector-teams-consentflow.png)

<span data-ttu-id="07384-137">**Benutzer-Zustimmungsfluss–** Dieser Bildschirm ist sowohl für persönliche als auch für Gruppenbereiche üblich.</span><span class="sxs-lookup"><span data-stu-id="07384-137">**User consent flow** - This screen is common for both personal and group scope.</span></span> <span data-ttu-id="07384-138">Aktivieren Sie hier das **Kontrollkästchen Zustimmung im** Namen Ihrer Organisation, und wählen Sie Akzeptieren **aus.**</span><span class="sxs-lookup"><span data-stu-id="07384-138">Here, select the **Consent on behalf of your organization** checkbox and choose **Accept**.</span></span>

![Berechtigungsdiagramm](../../../../assets/images/user-consent-flow.png)
