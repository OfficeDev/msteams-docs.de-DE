---
title: Azure-Bot-Kanalregistrierung
description: Beschreibt Azure-Botkanäle für die Registrierung
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta12
ms.openlocfilehash: 3cbbd204daf98f1c3528dcb6efcfde299a402912
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020949"
---
1. <span data-ttu-id="d791c-103">Wählen Sie [im Azure-Portal](https://ms.portal.azure.com/#home)unter Azure Services die Option **Ressource erstellen aus.**</span><span class="sxs-lookup"><span data-stu-id="d791c-103">In the [Azure portal](https://ms.portal.azure.com/#home), under Azure services, select **Create a resource**.</span></span>
1. <span data-ttu-id="d791c-104">Geben Sie im Suchfeld "Bot" ein.</span><span class="sxs-lookup"><span data-stu-id="d791c-104">In the search box enter "bot".</span></span> <span data-ttu-id="d791c-105">Wählen Sie in der Dropdownliste Bot **Channels Registration aus.**</span><span class="sxs-lookup"><span data-stu-id="d791c-105">And in the drop-down list, select **Bot Channels Registration**.</span></span>
1. <span data-ttu-id="d791c-106">Wählen Sie die **Schaltfläche Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="d791c-106">Select the **Create** button.</span></span>
1. <span data-ttu-id="d791c-107">Geben Sie **im Blatt Bot Channel Registration** die angeforderten Informationen zu Ihrem Bot an.</span><span class="sxs-lookup"><span data-stu-id="d791c-107">In the **Bot Channel Registration** blade, provide the requested information about your bot.</span></span>
1. <span data-ttu-id="d791c-108">Lassen Sie **das Feld** Messaging-Endpunkt vorerst leer, geben Sie nach der Bereitstellung des Bots die erforderliche URL ein.</span><span class="sxs-lookup"><span data-stu-id="d791c-108">Leave the **Messaging endpoint** box empty for now, you will enter the required URL after deploying the bot.</span></span> <span data-ttu-id="d791c-109">Die folgende Abbildung zeigt ein Beispiel für die Registrierungseinstellungen:</span><span class="sxs-lookup"><span data-stu-id="d791c-109">The following picture shows an example of the registration settings:</span></span>

    ![Registrierung von Bot-App-Kanälen](../../assets/images/authentication/auth-bot-channels-registration.png)

1. <span data-ttu-id="d791c-111">Klicken **Sie auf Microsoft App-ID und -Kennwort,** und erstellen Sie dann **Neu**.</span><span class="sxs-lookup"><span data-stu-id="d791c-111">Click **Microsoft App ID and password** and then **Create New**.</span></span>

    <span data-ttu-id="d791c-112">![Erstellen der Microsoft App-ID ](../../assets/images/authentication/CreateMicrosoftAppID.png) ![ Erstellen einer neuen Microsoft App-ID](../../assets/images/authentication/CreateNewMicrosoftAppID.png)</span><span class="sxs-lookup"><span data-stu-id="d791c-112">![Create Microsoft App ID](../../assets/images/authentication/CreateMicrosoftAppID.png) ![Create New Microsoft App ID](../../assets/images/authentication/CreateNewMicrosoftAppID.png)</span></span>    

1. <span data-ttu-id="d791c-113">Klicken **Sie im Link App-Registrierungsportal auf App-ID** erstellen.</span><span class="sxs-lookup"><span data-stu-id="d791c-113">Click **Create App ID in the App Registration Portal** link.</span></span>

   ![App-Registrierungen](../../assets/images/authentication/AppRegistration.png)
   
1. <span data-ttu-id="d791c-115">Klicken Sie im angezeigten **App-Registrierungsfenster** **oben** links auf die Registerkarte Neue Registrierung.</span><span class="sxs-lookup"><span data-stu-id="d791c-115">In the displayed **App registration** window, click the **New registration** tab in the upper left.</span></span>
1. <span data-ttu-id="d791c-116">Geben Sie den Namen der Botanwendung ein, die Sie registrieren, wir haben *BotTeamsAuth* verwendet (Sie müssen Ihren eigenen eindeutigen Namen auswählen).</span><span class="sxs-lookup"><span data-stu-id="d791c-116">Enter the name of the bot application you are registering, we used *BotTeamsAuth* (you need to select your own unique name).</span></span>
1. <span data-ttu-id="d791c-117">Wählen Sie **für** die unterstützten Kontotypen Konten in einem beliebigen Organisationsverzeichnis *(Beliebiges Azure AD-Verzeichnis - Multitenant) und persönlichen Microsoft-Konten (z. B. Skype, Xbox) aus.*</span><span class="sxs-lookup"><span data-stu-id="d791c-117">For the **Supported account types** select *Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)*.</span></span>
1. <span data-ttu-id="d791c-118">Klicken Sie auf **die Schaltfläche Registrieren.**</span><span class="sxs-lookup"><span data-stu-id="d791c-118">Click the **Register** button.</span></span> <span data-ttu-id="d791c-119">Nach Abschluss zeigt Azure die Seite *Übersicht* für die Anwendung an.</span><span class="sxs-lookup"><span data-stu-id="d791c-119">Once completed, Azure displays the *Overview* page for the application.</span></span>
1. <span data-ttu-id="d791c-120">Kopieren und speichern Sie in einer Datei den **Application (client)-ID-Wert.**</span><span class="sxs-lookup"><span data-stu-id="d791c-120">Copy and save to a file the **Application (client) ID** value.</span></span>
1. <span data-ttu-id="d791c-121">Klicken Sie im linken Bereich auf **Zertifikat und geheime Schlüssel.**</span><span class="sxs-lookup"><span data-stu-id="d791c-121">In the left panel, click **Certificate and secrets**.</span></span>
    1. <span data-ttu-id="d791c-122">Klicken *Sie unter Geheime* Clientgeheimnisse auf **Neuer Geheimer Clientgeheimnis.**</span><span class="sxs-lookup"><span data-stu-id="d791c-122">Under *Client secrets*, click **New client secret**.</span></span>
    1. <span data-ttu-id="d791c-123">Fügen Sie eine Beschreibung hinzu, um diesen geheimen Schlüssel von anderen Personen zu identifizieren, die Sie möglicherweise für diese App erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="d791c-123">Add a description to identify this secret from others you might need to create for this app.</span></span>
    1. <span data-ttu-id="d791c-124">Set *Expires* to your selection.</span><span class="sxs-lookup"><span data-stu-id="d791c-124">Set *Expires* to your selection.</span></span>
    1. <span data-ttu-id="d791c-125">Klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d791c-125">Click **Add**.</span></span>
    1. <span data-ttu-id="d791c-126">Kopieren Sie den geheimen Clientgeheimnis, und speichern Sie ihn in einer Datei.</span><span class="sxs-lookup"><span data-stu-id="d791c-126">Copy the client secret and save it to a file.</span></span>
1. <span data-ttu-id="d791c-127">Wechseln Sie zurück zum **Fenster Bot Channel Registration,** und kopieren Sie die *App-ID* und den geheimen *Client* in die Felder **Microsoft App-ID** **und** Kennwort.</span><span class="sxs-lookup"><span data-stu-id="d791c-127">Go back to the **Bot Channel Registration** window and copy the *App ID* and the *Client secret* in the **Microsoft App ID** and **Password** boxes, respectively.</span></span>
1. <span data-ttu-id="d791c-128">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="d791c-128">Click **OK**.</span></span>
1. <span data-ttu-id="d791c-129">Klicken Sie schließlich auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="d791c-129">Finally, click **Create**.</span></span>

<span data-ttu-id="d791c-130">Nachdem Azure die Registrierungsressource erstellt hat, wird sie in die Ressourcengruppenliste aufgenommen.</span><span class="sxs-lookup"><span data-stu-id="d791c-130">After Azure has created the registration resource it will be included in the resource group list.</span></span>  

![Registrierungsgruppe für Bot-App-Kanäle](~/assets/images/authentication/auth-bot-channels-registration-group.PNG)

<span data-ttu-id="d791c-132">Nachdem Die Registrierung Ihrer Botkanäle erstellt wurde, müssen Sie den Teams aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d791c-132">Once your bot channels registration is created, you'll need to enable the Teams channel.</span></span>

1. <span data-ttu-id="d791c-133">Wählen Sie [im Azure-Portal](https://ms.portal.azure.com/#home)unter Azure Services die gerade erstellte **Botkanalregistrierung** aus.</span><span class="sxs-lookup"><span data-stu-id="d791c-133">In the [Azure portal](https://ms.portal.azure.com/#home), under Azure services, select the **Bot Channel Registration** you just created.</span></span>
1. <span data-ttu-id="d791c-134">Klicken Sie im linken Bereich auf **Kanäle**.</span><span class="sxs-lookup"><span data-stu-id="d791c-134">In the left panel, click **Channels**.</span></span>
1. <span data-ttu-id="d791c-135">Klicken Sie auf Microsoft Teams Symbol, und wählen Sie dann **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="d791c-135">Click the Microsoft Teams icon, then choose **Save**.</span></span>
