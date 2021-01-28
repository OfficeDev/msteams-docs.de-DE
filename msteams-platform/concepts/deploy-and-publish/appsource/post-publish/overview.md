---
title: Verwalten und Unterstützen Ihrer veröffentlichten App
description: Was zu tun ist, nachdem Sie Ihre App veröffentlicht haben
ms.topic: how-to
keywords: Updateupdate für Zertifizierungs-App-Updatemanifest für Teams nach der Veröffentlichung
ms.openlocfilehash: ce63b840307f7e12a5cd05a1c67aed017cf6199b
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014327"
---
# <a name="maintain-and-support-your-published-app"></a><span data-ttu-id="fbcc7-104">Verwalten und Unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="fbcc7-104">Maintain and support your published app</span></span> 

<span data-ttu-id="fbcc7-105">Nachdem Ihre App genehmigt und im öffentlichen App-Katalog aufgeführt wurde, können Sie Ihre Reichweite erhöhen, indem Sie das Microsoft 365-App-Compliance-Programm abschließen oder eine Downloadschaltfläche auf Ihrer Website hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-105">After your app is approved and listed in the public app catalog, you can increase your reach by completing the Microsoft 365 App Compliance Program or by adding a download button on your website.</span></span>

## <a name="microsoft-365-certified"></a><span data-ttu-id="fbcc7-106">Microsoft 365-zertifiziert</span><span class="sxs-lookup"><span data-stu-id="fbcc7-106">Microsoft 365 Certified</span></span>

<span data-ttu-id="fbcc7-107">Das [Microsoft 365 App Compliance Program](./application-certification.md)ist ein dreistufiger Ansatz für die Sicherheit und Compliance von Apps.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-107">The [Microsoft 365 App Compliance Program](./application-certification.md), is a three tier approach to app security and compliance.</span></span> <span data-ttu-id="fbcc7-108">Jede Ebene baut auf der nächsten auf– sie bietet ein mehrschichtiges Programm, das die Anforderungen Ihrer Kunden erfüllt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-108">Each tier builds upon the next – offering a layered program to meet your customer’s needs.</span></span> <span data-ttu-id="fbcc7-109">Weitere Informationen zur Sicherheits- und Compliancelage von Teams-Apps finden Sie auf der Seite ["Compliance".](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps)</span><span class="sxs-lookup"><span data-stu-id="fbcc7-109">You can learn more about the security and compliance posture of Teams apps by visiting the [compliance page](https://docs.microsoft.com/microsoft-365-app-certification/teams/teams-apps).</span></span>

## <a name="add-a-download-button-to-your-product-site"></a><span data-ttu-id="fbcc7-110">Hinzufügen einer Downloadschaltfläche zu Ihrer Produktwebsite</span><span class="sxs-lookup"><span data-stu-id="fbcc7-110">Add a download button to your product site</span></span>

<span data-ttu-id="fbcc7-111">Wenn Sich Ihre App im globalen Microsoft Teams Store befindet, können Sie einen Link für Ihre Website generieren, der Teams startet und ein Zustimmungs- und Installationsdialogfeld für Benutzer zum Hinzufügen der App zeigt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-111">If your app is in the Microsoft Teams global store, you can generate a link for your website that launches Teams and shows a consent and installation dialog for users to add the app.</span></span>
<span data-ttu-id="fbcc7-112">Das Format ist:  `https://teams.microsoft.com/l/app/<appId>` wobei appID die GUID ist, die sie im übermittelten Manifest deklarieren.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-112">The format is:  `https://teams.microsoft.com/l/app/<appId>` where appID is the GUID they declare in the submitted manifest.</span></span>
<span data-ttu-id="fbcc7-113">Beispiel: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` Ist der Link zum Installieren von Trello.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-113">Example: `https://teams.microsoft.com/l/app/49e6f432-d79c-49e8-94f7-89b94f3672fd` is the link to install Trello.</span></span>

## <a name="updating-your-existing-teams-app"></a><span data-ttu-id="fbcc7-114">Aktualisieren Ihrer vorhandenen Teams-App</span><span class="sxs-lookup"><span data-stu-id="fbcc7-114">Updating your existing Teams app</span></span>

* <span data-ttu-id="fbcc7-115">Verwenden Sie nicht die Schaltfläche *"Neue App hinzufügen",* um Ihre App erneut zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-115">Do not use the *Add a new app* button to resubmit your app.</span></span> <span data-ttu-id="fbcc7-116">Verwenden Sie stattdessen die Kachel für Ihre App auf der Registerkarte "Übersicht".</span><span class="sxs-lookup"><span data-stu-id="fbcc7-116">Use the tile for your app on the Overview tab instead.</span></span>
* <span data-ttu-id="fbcc7-117">Die appId im aktualisierten Manifest sollte mit der im aktuellen Manifest identisch sein, mit einer inkrementierten Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-117">The appId in the updated manifest should be the same as in the current manifest, with an incremented version number.</span></span>
* <span data-ttu-id="fbcc7-118">Erhöhen Sie Ihre Versionsnummer im Manifest, wenn Sie Änderungen an Ihrer Übermittlung vornehmen, einschließlich des App-Namens oder metadaten im Manifest.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-118">Increment your version number in the manifest if you make any changes to your submission including app name or any metadata in the manifest.</span></span>
* <span data-ttu-id="fbcc7-119">Aktualisierte Übermittlungen sind erforderlich, um einen neuen Überprüfungs- und Überprüfungsprozess zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-119">Updated submissions are required to undergo a new review and validation process.</span></span>

## <a name="app-updates-and-the-user-consent-flow"></a><span data-ttu-id="fbcc7-120">App-Updates und der Benutzer-Zustimmungsfluss</span><span class="sxs-lookup"><span data-stu-id="fbcc7-120">App updates and the user consent flow</span></span>

<span data-ttu-id="fbcc7-121">Wenn ein Benutzer Ihre Anwendung zu einem der ersten Dinge installiert, muss er der App die Berechtigung zum Zugriff auf die Dienste und Informationen erteilen, die die App für ihre Arbeit benötigt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-121">When a user installs your application one of the first things they do is consent to give the app permission to access the services and information that the app needs to do its job.</span></span> <span data-ttu-id="fbcc7-122">In den meisten Fällen wird nach Abschluss eines App-Updates die neue Version automatisch für Endbenutzer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-122">In most cases, after you complete an app update the new version will automatically appear for end users.</span></span> <span data-ttu-id="fbcc7-123">Es gibt jedoch einige Updates für das [Teams-App-Manifest,](../../../../resources/schema/manifest-schema.md) die die Benutzerakzeptanz erfordern und dieses Zustimmungsverhalten erneut auslösen können:</span><span class="sxs-lookup"><span data-stu-id="fbcc7-123">However, there are some updates to the [Teams app manifest](../../../../resources/schema/manifest-schema.md) that require user acceptance to complete and can re-trigger this consent behavior:</span></span>

 >[!div class="checklist"]
>
> * <span data-ttu-id="fbcc7-124">Ein Bot wurde hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-124">A bot was added or removed.</span></span>
> * <span data-ttu-id="fbcc7-125">Der eindeutige Wert eines vorhandenen `botId` Bots wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-125">An existing bot's unique `botId` value changed.</span></span>
> * <span data-ttu-id="fbcc7-126">Der boolesche Wert eines `isNotificationOnly` vorhandenen Bots wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-126">An existing bot's `isNotificationOnly` boolean value changed.</span></span>
> * <span data-ttu-id="fbcc7-127">Der boolesche Wert eines `supportsFiles` vorhandenen Bots wurde geändert.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-127">An existing bot's `supportsFiles` boolean value changed.</span></span>
> * <span data-ttu-id="fbcc7-128">Eine Messagingerweiterung ( `composeExtensions` ) wurde hinzugefügt oder entfernt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-128">A messaging extension (`composeExtensions`) was added or removed.</span></span>
> * <span data-ttu-id="fbcc7-129">Ein neuer Connector wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-129">A new connector was added.</span></span>
> * <span data-ttu-id="fbcc7-130">Eine neue statische/persönliche Registerkarte wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-130">A new static/personal tab was added.</span></span>
> * <span data-ttu-id="fbcc7-131">Eine neue konfigurierbare Gruppen-/Kanalregisterkarte wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-131">A new configurable group/channel tab was added.</span></span>
> * <span data-ttu-id="fbcc7-132">Die `webApplicationInfo` Werte wurden geändert.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-132">The `webApplicationInfo` values changed.</span></span>
>

### <a name="images-of-user-consent-flow"></a><span data-ttu-id="fbcc7-133">Bilder des Zustimmungsflusses des Benutzers:</span><span class="sxs-lookup"><span data-stu-id="fbcc7-133">Images of user consent flow:</span></span>

<span data-ttu-id="fbcc7-134">**Einrichten eines Connectors** – Dieser Bildschirm wird nur für Benutzer von Teams angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-134">**Set up a connector** —  This screen will appear only for Teams users.</span></span>

![Zustimmungsfluss einrichten eines Konnektordiagramms](../../../../assets/images/connector-teams-consentflow.png)

<span data-ttu-id="fbcc7-136">**Benutzer-Zustimmungsfluss:** Dieser Bildschirm ist sowohl für persönliche als auch für Gruppenbereiche üblich.</span><span class="sxs-lookup"><span data-stu-id="fbcc7-136">**User consent flow** - This screen is common for both personal and group scope.</span></span> <span data-ttu-id="fbcc7-137">Aktivieren Sie hier das **Kontrollkästchen "Zustimmung im Auftrag Ihrer Organisation",** und wählen Sie **"Annehmen" aus.**</span><span class="sxs-lookup"><span data-stu-id="fbcc7-137">Here, select the **Consent on behalf of your organization** checkbox and choose **Accept**.</span></span>

![Berechtigungsdiagramm](../../../../assets/images/user-consent-flow.png)
