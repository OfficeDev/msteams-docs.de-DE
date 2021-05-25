---
title: Empfangen aller Kanalnachrichten mit RSC
author: surbhigupta12
description: Empfangen aller Kanalnachrichten mit RSC-Berechtigungen
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 833bdbc015cf852fcd899ce4e75f742448b89978
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631326"
---
# <a name="receive-all-channel-messages-with-rsc"></a><span data-ttu-id="0f5d9-103">Empfangen aller Kanalnachrichten mit RSC</span><span class="sxs-lookup"><span data-stu-id="0f5d9-103">Receive all channel messages with RSC</span></span>

> [!NOTE]
> <span data-ttu-id="0f5d9-104">Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../../../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-104">This feature is currently available in [public developer preview](../../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="0f5d9-105">Das ressourcenspezifische Berechtigungsmodell (Resource-Specific Consent, RSC), das ursprünglich für Teams Graph-APIs entwickelt wurde, wurde nun auf Botszenarien erweitert.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-105">The resource-specific consent (RSC) permissions model, originally developed for Teams Graph APIs, is now extended to bot scenarios.</span></span>

<span data-ttu-id="0f5d9-106">Derzeit können Bots nur Benutzerkanalnachrichten empfangen, wenn sie @mentioned.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-106">Currently, bots can only receive user channel messages when they are @mentioned.</span></span> <span data-ttu-id="0f5d9-107">Mithilfe von RSC können Sie teambesitzer nun bitten, einem Bot zu zustimmen, Benutzernachrichten über Standardkanäle in einem Team zu empfangen, ohne dass @mentioned.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-107">Using RSC, you can now request team owners to consent for a bot to receive user messages across standard channels in a team without being @mentioned.</span></span> <span data-ttu-id="0f5d9-108">Diese Funktion wird durch Angeben der Berechtigung im Manifest einer `ChannelMessage.Read.Group` RSC-aktivierten Teams aktiviert.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-108">This capability is enabled by specifying the `ChannelMessage.Read.Group` permission in the manifest of an RSC enabled Teams app.</span></span> <span data-ttu-id="0f5d9-109">Nach der Konfiguration können Teambesitzer während des App-Installationsvorgangs ihre Zustimmung erteilen.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-109">After configuration, team owners can grant consent during the app installation process.</span></span>

<span data-ttu-id="0f5d9-110">Weitere Informationen zum Aktivieren von RSC für Ihre App finden Sie unter [ressourcenspezifische](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest)Zustimmung in Teams .</span><span class="sxs-lookup"><span data-stu-id="0f5d9-110">For more information about enabling RSC for your app, see [resource-specific consent in Teams](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#update-your-teams-app-manifest).</span></span>

## <a name="enable-bots-to-receive-all-channel-messages"></a><span data-ttu-id="0f5d9-111">Aktivieren von Bots zum Empfangen aller Kanalnachrichten</span><span class="sxs-lookup"><span data-stu-id="0f5d9-111">Enable bots to receive all channel messages</span></span>

<span data-ttu-id="0f5d9-112">Die `ChannelMessage.Read.Group` RSC-Berechtigung wird auf Bots erweitert.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-112">The `ChannelMessage.Read.Group` RSC permission is extended to bots.</span></span> <span data-ttu-id="0f5d9-113">Mit dieser Berechtigung können Graph-Anwendungen mit Zustimmung des Benutzers alle Nachrichten in einer Unterhaltung und Bots alle Kanalnachrichten empfangen, ohne dass sie @mentioned.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-113">With user consent, this permission allows graph applications to get all messages in a conversation and bots to receive all channel messages without being @mentioned.</span></span>

## <a name="update-app-manifest"></a><span data-ttu-id="0f5d9-114">Aktualisieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="0f5d9-114">Update app manifest</span></span>

<span data-ttu-id="0f5d9-115">Damit Ihr Bot alle Kanalnachrichten empfangen kann, muss RSC im Teams-App-Manifest mit der in der `ChannelMessage.Read.Group` Eigenschaft angegebenen Berechtigung konfiguriert `webApplicationInfo` werden.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-115">For your bot to receive all channel messages, RSC must be configured in the Teams app manifest with the `ChannelMessage.Read.Group` permission specified in the `webApplicationInfo` property.</span></span>

![Aktualisieren des App-Manifests](~/bots/how-to/conversations/Media/appmanifest.png)

<span data-ttu-id="0f5d9-117">Es folgt ein Beispiel für das `webApplicationInfo` Objekt:</span><span class="sxs-lookup"><span data-stu-id="0f5d9-117">The following is an example of the `webApplicationInfo` object:</span></span>

* <span data-ttu-id="0f5d9-118">**id**: Ihre Azure Active Directory (AAD)-App-ID.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-118">**id**: Your Azure Active Directory (AAD) app ID.</span></span> <span data-ttu-id="0f5d9-119">Dies kann mit Ihrer Bot-ID identisch sein.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-119">This can be the same as your bot ID.</span></span>
* <span data-ttu-id="0f5d9-120">**resource**: Any string.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-120">**resource**: Any string.</span></span> <span data-ttu-id="0f5d9-121">Dieses Feld hat keinen Vorgang in RSC, muss jedoch hinzugefügt werden und über einen Wert verfügen, um Fehlerantworten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-121">This field has no operation in RSC, but must be added and have a value to avoid error response.</span></span>
* <span data-ttu-id="0f5d9-122">**applicationPermissions**: RSC-Berechtigungen für Ihre App `ChannelMessage.Read.Group` mit müssen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-122">**applicationPermissions**: RSC permissions for your app with `ChannelMessage.Read.Group` must be specified.</span></span> <span data-ttu-id="0f5d9-123">Weitere Informationen finden Sie unter [ressourcenspezifische Berechtigungen](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).</span><span class="sxs-lookup"><span data-stu-id="0f5d9-123">For more information, see [resource-specific permissions](/microsoftteams/platform/graph-api/rsc/resource-specific-consent#resource-specific-permissions).</span></span>

<span data-ttu-id="0f5d9-124">Der folgende Code enthält ein Beispiel für das App-Manifest:</span><span class="sxs-lookup"><span data-stu-id="0f5d9-124">The following code provides an example of the app manifest:</span></span>

```json
"webApplicationInfo": {
"id": "XXxxXXXXX-XxXX-xXXX-XXxx-XXXXXXXxxxXX",
"resource": "https://AnyString",
"applicationPermissions": [
"ChannelMessage.Read.Group"
    ]
  }
```

## <a name="sideload-in-a-team-to-test"></a><span data-ttu-id="0f5d9-125">Querladen in einem zu testenden Team</span><span class="sxs-lookup"><span data-stu-id="0f5d9-125">Sideload in a team to test</span></span>

<span data-ttu-id="0f5d9-126">So laden Sie in einem Team quer, um zu testen, ob alle Kanalnachrichten in einem Team mit RSC empfangen werden, ohne dass @mentioned:</span><span class="sxs-lookup"><span data-stu-id="0f5d9-126">To sideload in a team to test, whether all channel messages in a team with RSC are received without being @mentioned:</span></span>

1. <span data-ttu-id="0f5d9-127">Wählen Oder erstellen Sie ein Team.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-127">Select or create a team.</span></span>
1. <span data-ttu-id="0f5d9-128">Wählen Sie die ellipsen &#x25CF;&#x25CF;&#x25CF; linken Bereich aus.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-128">Select the ellipses &#x25CF;&#x25CF;&#x25CF; from the left pane.</span></span> <span data-ttu-id="0f5d9-129">Das Dropdownmenü wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-129">The drop-down menu appears.</span></span>
1. <span data-ttu-id="0f5d9-130">Wählen **Sie team verwalten** im Dropdownmenü aus.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-130">Select **Manage team** from the drop-down menu.</span></span> <span data-ttu-id="0f5d9-131">Die Details werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-131">The details appear.</span></span>

   ![Verwalten von Apps im Team](~/bots/how-to/conversations/Media/managingteam.png)

1. <span data-ttu-id="0f5d9-133">Wählen Sie **Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-133">Select **Apps**.</span></span> <span data-ttu-id="0f5d9-134">Es werden mehrere Apps angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-134">Multiple apps appear.</span></span>
1. <span data-ttu-id="0f5d9-135">Wählen **Hochladen eine benutzerdefinierte App aus** der unteren rechten Ecke aus.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-135">Select **Upload a custom app** from the lower right corner.</span></span>

    ![Hochladen benutzerdefinierter Apps](~/bots/how-to/conversations/Media/uploadingcustomapp.png)

1. <span data-ttu-id="0f5d9-137">Wählen Sie das App-Paket im Dialogfeld **Öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-137">Select the app package from the **Open** dialog box.</span></span>
1. <span data-ttu-id="0f5d9-138">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-138">Select **Open**.</span></span>

    ![Auswählen des App-Pakets](~/bots/how-to/conversations/Media/selectapppackage.png)

1. <span data-ttu-id="0f5d9-140">Wählen **Sie Im** Popup app-Details hinzufügen aus, um den Bot zu Ihrem ausgewählten Team hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-140">Select **Add** from the app details pop-up, to add the bot to your selected team.</span></span>

    ![Hinzufügen des Bots](~/bots/how-to/conversations/Media/addingbot.png)

1. <span data-ttu-id="0f5d9-142">Wählen Sie einen Kanal aus, und geben Sie eine Nachricht im Kanal für Ihren Bot ein.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-142">Select a channel and enter a message in the channel for your bot.</span></span>

    <span data-ttu-id="0f5d9-143">Der Bot empfängt die Nachricht, ohne dass @mentioned.</span><span class="sxs-lookup"><span data-stu-id="0f5d9-143">The bot receives the message without being @mentioned.</span></span>

    ![Bot empfängt Nachricht](~/bots/how-to/conversations/Media/botreceivingmessage.png)

## <a name="see-also"></a><span data-ttu-id="0f5d9-145">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="0f5d9-145">See also</span></span>

* [<span data-ttu-id="0f5d9-146">Bot-Unterhaltungen</span><span class="sxs-lookup"><span data-stu-id="0f5d9-146">Bot conversations</span></span>](/microsoftteams/platform/bots/how-to/conversations/conversation-basics)
* [<span data-ttu-id="0f5d9-147">Ressourcenspezifische Zustimmung</span><span class="sxs-lookup"><span data-stu-id="0f5d9-147">Resource-specific consent</span></span>](/microsoftteams/resource-specific-consent)
* [<span data-ttu-id="0f5d9-148">Testen der ressourcenspezifischen Zustimmung</span><span class="sxs-lookup"><span data-stu-id="0f5d9-148">Test resource-specific consent</span></span>](/microsoftteams/platform/graph-api/rsc/test-resource-specific-consent)
* [<span data-ttu-id="0f5d9-149">Hochladen benutzerdefinierte App in Teams</span><span class="sxs-lookup"><span data-stu-id="0f5d9-149">Upload custom app in Teams</span></span>](~/concepts/deploy-and-publish/apps-upload.md)
