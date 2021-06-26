---
title: Erstellen eines eingehenden Webhooks
author: laujan
description: beschreibt, wie eingehende Webhooks zu Teams App hinzugefügt und externe Anforderungen an Teams mit eingehenden Webhooks gesendet werden.
keywords: Teams-Registerkarten für ausgehenden Webhook
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 53fe9725148579325386fa4677bebb61fdb72c56
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140118"
---
# <a name="create-incoming-webhook"></a><span data-ttu-id="cc70a-104">Erstellen eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="cc70a-104">Create Incoming Webhook</span></span>

<span data-ttu-id="cc70a-105">Mit eingehendem Webhook können externe Apps Inhalte in Teams Kanälen freigeben.</span><span class="sxs-lookup"><span data-stu-id="cc70a-105">Incoming Webhook allows any external apps to share content in Teams channels.</span></span> <span data-ttu-id="cc70a-106">Diese Webhooks werden als Tracking- und Benachrichtigungstools verwendet.</span><span class="sxs-lookup"><span data-stu-id="cc70a-106">These webhooks are used as tracking and notifying tools.</span></span> <span data-ttu-id="cc70a-107">Sie stellen eine eindeutige URL bereit, an die Sie eine JSON-Nutzlast mit einer Nachricht im Kartenformat senden.</span><span class="sxs-lookup"><span data-stu-id="cc70a-107">They provide a unique URL, to which you send a JSON payload with a message in card format.</span></span> <span data-ttu-id="cc70a-108">Karten sind Benutzeroberflächencontainer, die Inhalte und Aktionen im Zusammenhang mit einem einzelnen Thema enthalten.</span><span class="sxs-lookup"><span data-stu-id="cc70a-108">Cards are user interface containers that include content and actions related to a single topic.</span></span> <span data-ttu-id="cc70a-109">Teams Karten in den folgenden Funktionen verwenden:</span><span class="sxs-lookup"><span data-stu-id="cc70a-109">Teams use cards within the following capabilities:</span></span>

* <span data-ttu-id="cc70a-110">Bots</span><span class="sxs-lookup"><span data-stu-id="cc70a-110">Bots</span></span>
* <span data-ttu-id="cc70a-111">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="cc70a-111">Messaging extensions</span></span>
* <span data-ttu-id="cc70a-112">Connectors</span><span class="sxs-lookup"><span data-stu-id="cc70a-112">Connectors</span></span>

## <a name="key-features-of-incoming-webhook"></a><span data-ttu-id="cc70a-113">Wichtige Features des eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="cc70a-113">Key features of Incoming Webhook</span></span>

<span data-ttu-id="cc70a-114">Die folgende Tabelle enthält die Features und die Beschreibung des eingehenden Webhooks:</span><span class="sxs-lookup"><span data-stu-id="cc70a-114">The following table provides the features and description of Incoming Webhook:</span></span>

| <span data-ttu-id="cc70a-115">Features</span><span class="sxs-lookup"><span data-stu-id="cc70a-115">Features</span></span> | <span data-ttu-id="cc70a-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cc70a-116">Description</span></span> |
| ------- | ----------- |
|<span data-ttu-id="cc70a-117">Adaptive Karten mit einem eingehenden Webhook</span><span class="sxs-lookup"><span data-stu-id="cc70a-117">Adaptive Cards using an Incoming Webhook</span></span>|<span data-ttu-id="cc70a-118">Adaptive Karten können über eingehende Webhooks gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="cc70a-118">Adaptive Cards can be sent through Incoming Webhooks.</span></span> <span data-ttu-id="cc70a-119">Weitere Informationen finden Sie unter [Senden adaptiver Karten mit eingehenden Webhooks.](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook)</span><span class="sxs-lookup"><span data-stu-id="cc70a-119">For more information, see [Send Adaptive Cards using Incoming Webhooks](../../webhooks-and-connectors/how-to/connectors-using.md#send-adaptive-cards-using-an-incoming-webhook).</span></span>|
|<span data-ttu-id="cc70a-120">Unterstützung für Aktion erfordernde Nachrichten</span><span class="sxs-lookup"><span data-stu-id="cc70a-120">Actionable messaging support</span></span>|<span data-ttu-id="cc70a-121">Aktion erfordernde Nachrichtenkarten werden in allen Office 365-Gruppen einschließlich Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cc70a-121">Actionable message cards are supported in all Office 365 groups including Teams.</span></span> <span data-ttu-id="cc70a-122">Wenn Sie Nachrichten über Karten senden, müssen Sie das Kartenformat für Aktionen erfordernde Nachrichten verwenden.</span><span class="sxs-lookup"><span data-stu-id="cc70a-122">If you send messages through cards, you must use the actionable message card format.</span></span> <span data-ttu-id="cc70a-123">Weitere Informationen finden Sie unter [Legacy-Referenz für Nachrichtenkarten](/outlook/actionable-messages/message-card-reference) mit Aktionen und [Nachrichtenkarten-Playground.](https://messagecardplayground.azurewebsites.net)</span><span class="sxs-lookup"><span data-stu-id="cc70a-123">For more information, see [legacy actionable message card reference](/outlook/actionable-messages/message-card-reference) and [message card playground](https://messagecardplayground.azurewebsites.net).</span></span>|
|<span data-ttu-id="cc70a-124">Unabhängige HTTPS-Messaging-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="cc70a-124">Independent HTTPS messaging support</span></span>|<span data-ttu-id="cc70a-125">Karten stellen Informationen klar und konsistent bereit.</span><span class="sxs-lookup"><span data-stu-id="cc70a-125">Cards provide information clearly and consistently.</span></span> <span data-ttu-id="cc70a-126">Jedes Tool oder Framework, das HTTPS POST-Anforderungen senden kann, kann Nachrichten über einen eingehenden Webhook an Teams senden.</span><span class="sxs-lookup"><span data-stu-id="cc70a-126">Any tool or framework that can send HTTPS POST requests, can send messages to Teams through an Incoming Webhook.</span></span>|
|<span data-ttu-id="cc70a-127">Markdown-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="cc70a-127">Markdown support</span></span>|<span data-ttu-id="cc70a-128">Alle Textfelder in Aktion erfordernden Nachrichtenkarten unterstützen grundlegendes Markdown.</span><span class="sxs-lookup"><span data-stu-id="cc70a-128">All text fields in actionable messaging cards support basic Markdown.</span></span> <span data-ttu-id="cc70a-129">Verwenden Sie kein HTML-Markup in Ihren Karten.</span><span class="sxs-lookup"><span data-stu-id="cc70a-129">Do not use HTML markup in your cards.</span></span> <span data-ttu-id="cc70a-130">HTML wird ignoriert und als reiner Text behandelt.</span><span class="sxs-lookup"><span data-stu-id="cc70a-130">HTML is ignored and treated as plain text.</span></span>|
|<span data-ttu-id="cc70a-131">Bereichskonfiguration</span><span class="sxs-lookup"><span data-stu-id="cc70a-131">Scoped configuration</span></span>|<span data-ttu-id="cc70a-132">Eingehender Webhook ist auf Kanalebene beschränkt und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="cc70a-132">Incoming Webhook is scoped and configured at the channel level.</span></span>|
|<span data-ttu-id="cc70a-133">Sichere Ressourcendefinitionen</span><span class="sxs-lookup"><span data-stu-id="cc70a-133">Secure resource definitions</span></span>|<span data-ttu-id="cc70a-134">Nachrichten werden als JSON-Nutzlast formatiert.</span><span class="sxs-lookup"><span data-stu-id="cc70a-134">Messages are formatted as JSON payloads.</span></span> <span data-ttu-id="cc70a-135">Diese deklarative Messagingstruktur verhindert das Einfügen von schädlichem Code.</span><span class="sxs-lookup"><span data-stu-id="cc70a-135">This declarative messaging structure prevents the insertion of malicious code.</span></span>|

> [!NOTE]
> * <span data-ttu-id="cc70a-136">Teams Bots, Messaging-Erweiterungen, eingehender Webhook und bot Framework unterstützen adaptive Karten, ein offenes kartenübergreifendes Plattformframework.</span><span class="sxs-lookup"><span data-stu-id="cc70a-136">Teams bots, messaging extensions, Incoming Webhook, and the Bot Framework support Adaptive Cards, an open cross card platform framework.</span></span> <span data-ttu-id="cc70a-137">Derzeit unterstützen [Teams Connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) keine adaptiven Karten.</span><span class="sxs-lookup"><span data-stu-id="cc70a-137">Currently, [Teams connectors](../../webhooks-and-connectors/how-to/connectors-creating.md) do not support Adaptive Cards.</span></span> <span data-ttu-id="cc70a-138">Es ist jedoch möglich, einen [Fluss](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) zu erstellen, der adaptive Karten an einen Teams-Kanal sendet.</span><span class="sxs-lookup"><span data-stu-id="cc70a-138">However, it is possible to create a [flow](https://flow.microsoft.com/blog/microsoft-flow-in-microsoft-teams/) that posts Adaptive Cards to a Teams channel.</span></span>
> * <span data-ttu-id="cc70a-139">Weitere Informationen zu Karten und Webhooks finden Sie unter [Adaptive Karten und eingehende Webhooks.](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks)</span><span class="sxs-lookup"><span data-stu-id="cc70a-139">For more information on cards and webhooks, see [Adaptive cards and Incoming Webhooks](~/task-modules-and-cards/what-are-cards.md#adaptive-cards-and-incoming-webhooks).</span></span>

## <a name="create-incoming-webhook"></a><span data-ttu-id="cc70a-140">Erstellen eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="cc70a-140">Create Incoming Webhook</span></span>

<span data-ttu-id="cc70a-141">**So fügen Sie einem Teams Kanal einen eingehenden Webhook hinzu**</span><span class="sxs-lookup"><span data-stu-id="cc70a-141">**To add an Incoming Webhook to a Teams channel**</span></span>

1. <span data-ttu-id="cc70a-142">Wechseln Sie zu dem Kanal, in dem Sie den Webhook hinzufügen möchten, und wählen Sie &#8226;&#8226;&#8226; **Weitere Optionen** in der oberen Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="cc70a-142">Go to the channel where you want to add the webhook and select &#8226;&#8226;&#8226; **More options** from the top navigation bar.</span></span>
1. <span data-ttu-id="cc70a-143">Wählen Sie **connectors** aus dem Dropdownmenü aus:</span><span class="sxs-lookup"><span data-stu-id="cc70a-143">Select **Connectors** from the dropdown menu:</span></span>

    ![Connector auswählen](~/assets/images/connectors.png)

1. <span data-ttu-id="cc70a-145">Suchen Sie nach **eingehendem Webhook,** und wählen Sie **"Hinzufügen"** aus.</span><span class="sxs-lookup"><span data-stu-id="cc70a-145">Search for **Incoming Webhook** and select **Add**.</span></span>
1. <span data-ttu-id="cc70a-146">Wählen Sie **"Konfigurieren",** geben Sie einen Namen an, und laden Sie bei Bedarf ein Bild für Ihren Webhook hoch:</span><span class="sxs-lookup"><span data-stu-id="cc70a-146">Select **Configure**, provide a name, and upload an image for your webhook if required:</span></span>

    ![Schaltfläche "Konfigurieren"](~/assets/images/configure.png)

1. <span data-ttu-id="cc70a-148">Im Dialogfeld wird eine eindeutige URL angezeigt, die dem Kanal zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="cc70a-148">The dialog window presents a unique URL that maps to the channel.</span></span> <span data-ttu-id="cc70a-149">Kopieren und speichern Sie die Webhook-URL, um Informationen an Microsoft Teams zu senden und **"Fertig"** auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="cc70a-149">Copy and save the webhook URL, to send information to Microsoft Teams and select **Done**:</span></span>

    ![Eindeutige URL](~/assets/images/url.png)

<span data-ttu-id="cc70a-151">Der Webhook ist im Teams Kanal verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cc70a-151">The webhook is available in the Teams channel.</span></span>

> [!NOTE]
> <span data-ttu-id="cc70a-152">Wählen Sie in Teams **Einstellungen**  >  **Mitgliedsberechtigungen** aus, damit Mitglieder Connectors  >  **erstellen, aktualisieren und entfernen können,** damit jedes Teammitglied einen Connector hinzufügen, ändern oder löschen kann.</span><span class="sxs-lookup"><span data-stu-id="cc70a-152">In Teams, select **Settings** > **Member permissions** > **Allow members to create, update, and remove connectors**, so that any team member can add, modify, or delete a connector.</span></span>

## <a name="remove-incoming-webhook"></a><span data-ttu-id="cc70a-153">Entfernen des eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="cc70a-153">Remove Incoming Webhook</span></span>

<span data-ttu-id="cc70a-154">**So entfernen Sie einen eingehenden Webhook aus einem Teams Kanal**</span><span class="sxs-lookup"><span data-stu-id="cc70a-154">**To remove an Incoming Webhook from a Teams channel**</span></span>

1. <span data-ttu-id="cc70a-155">Wechseln Sie zum Kanal.</span><span class="sxs-lookup"><span data-stu-id="cc70a-155">Go to the channel.</span></span>
1. <span data-ttu-id="cc70a-156">Wählen Sie in der oberen Navigationsleiste &#8226;&#8226;&#8226; **Weitere Optionen** aus.</span><span class="sxs-lookup"><span data-stu-id="cc70a-156">Select &#8226;&#8226;&#8226; **More options** from the top navigation bar.</span></span>
1. <span data-ttu-id="cc70a-157">Wählen Sie im Dropdownmenü **Connectors** aus.</span><span class="sxs-lookup"><span data-stu-id="cc70a-157">Select **Connectors** from the dropdown menu.</span></span>
1. <span data-ttu-id="cc70a-158">Wählen Sie auf der linken Seite unter **Verwalten** die Option **"Konfiguriert"** aus.</span><span class="sxs-lookup"><span data-stu-id="cc70a-158">On the left, under **Manage**, select **Configured**.</span></span>
1. <span data-ttu-id="cc70a-159">Wählen Sie die **< *1*> Konfiguriert aus,** um eine Liste Ihrer aktuellen Connectors anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="cc70a-159">Select the **<*1*> Configured** to see a list of your current connectors:</span></span>

    ![Konfigurierter Webhook](~/assets/images/configured.png)

1. <span data-ttu-id="cc70a-161">Wählen Sie neben dem Connector, den Sie entfernen möchten, die Option **"Verwalten"** aus:</span><span class="sxs-lookup"><span data-stu-id="cc70a-161">Select **Manage** next to the connector that you want to remove:</span></span>

    ![Verwalten von Webhook](~/assets/images/manage.png)

1. <span data-ttu-id="cc70a-163">Wählen Sie **"Entfernen" aus:**</span><span class="sxs-lookup"><span data-stu-id="cc70a-163">Select **Remove**:</span></span>

    ![Entfernen von Webhook](~/assets/images/remove.png)

    <span data-ttu-id="cc70a-165">Das Dialogfeld Konfiguration **entfernen** wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="cc70a-165">The **Remove Configuration** dialog box appears:</span></span>

    ![Entfernen der Konfiguration](~/assets/images/removeconfiguration.png)

1. <span data-ttu-id="cc70a-167">Füllen Sie die Felder und Kontrollkästchen des Dialogfelds aus, und wählen Sie **"Entfernen" aus:**</span><span class="sxs-lookup"><span data-stu-id="cc70a-167">Complete the dialog box fields and checkboxes and select **Remove**:</span></span>

    ![Endgültiges Entfernen](~/assets/images/finalremove.png)

    <span data-ttu-id="cc70a-169">Der Webhook wird aus dem Teams-Kanal entfernt.</span><span class="sxs-lookup"><span data-stu-id="cc70a-169">The webhook is removed from the Teams channel.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc70a-170">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cc70a-170">See also</span></span>

* [<span data-ttu-id="cc70a-171">Erstellen eines ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="cc70a-171">Create an Outgoing Webhook</span></span>](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [<span data-ttu-id="cc70a-172">Erstellen eines Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="cc70a-172">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="cc70a-173">Erstellen und Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="cc70a-173">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)
