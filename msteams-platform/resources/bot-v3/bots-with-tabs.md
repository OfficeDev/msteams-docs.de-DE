---
title: Kombinieren von Bots mit Registerkarten
description: Beschreibt, wie Registerkarten und Bots gemeinsam verwendet werden
keywords: Teams Bots-Tabs-Entwicklung
ms.date: 03/15/2018
ms.openlocfilehash: 59ae8bc01f82c70dd7ea6869cb870e26acae1293
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674376"
---
# <a name="combine-bots-with-tabs"></a><span data-ttu-id="096d7-104">Kombinieren von Bots mit Registerkarten</span><span class="sxs-lookup"><span data-stu-id="096d7-104">Combine bots with tabs</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="096d7-105">Bots und Registerkarten funktionieren gut zusammen und werden häufig in einem einzigen Back-End-Dienst kombiniert.</span><span class="sxs-lookup"><span data-stu-id="096d7-105">Bots and tabs work well together, and are often combined into a single back-end service.</span></span> <span data-ttu-id="096d7-106">In diesem Abschnitt werden bewährte Methoden und allgemeine Muster für die Verwendung von Registerkarten und Bots zusammen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="096d7-106">This section describes best practices and common patterns for using tabs and bots together.</span></span>

## <a name="associating-user-identities-across-bot-and-tab"></a><span data-ttu-id="096d7-107">Zuordnen von Benutzeridentitäten über bot und Tab</span><span class="sxs-lookup"><span data-stu-id="096d7-107">Associating user identities across bot and tab</span></span>

<span data-ttu-id="096d7-108">Beispiel: angenommen, ihre Tab-Anwendung verwendet ein proprietäres ID-System, um den Inhalt zu sichern.</span><span class="sxs-lookup"><span data-stu-id="096d7-108">For example: Suppose your tab application uses a proprietary ID system to secure its content.</span></span> <span data-ttu-id="096d7-109">Angenommen, Sie haben auch einen bot, der mit dem Benutzer interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="096d7-109">Suppose you also have a bot that can interact with the user.</span></span> <span data-ttu-id="096d7-110">In der Regel sollten Sie Inhalte auf der Registerkarte anzeigen, die speziell für den Benutzer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="096d7-110">Typically, you’ll want to show content in the tab that is specific to the viewing user.</span></span> <span data-ttu-id="096d7-111">Die Herausforderung besteht darin, dass sich die Benutzer-ID in Ihrem System wahrscheinlich von der Benutzer-ID von Microsoft Teams unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="096d7-111">The challenge is that the user ID in your system is likely different from the Microsoft Teams user ID.</span></span> <span data-ttu-id="096d7-112">Wie ordnen Sie diese beiden Identitäten zu?</span><span class="sxs-lookup"><span data-stu-id="096d7-112">So how do you associate these two identities?</span></span>
<span data-ttu-id="096d7-113">Im Allgemeinen besteht der empfohlene Ansatz darin, den Benutzer mit dem gleichen Identitätssystem, mit dem die Authentifizierung für die Registerkarteninhalte erfolgt, mit dem bot zu signieren.</span><span class="sxs-lookup"><span data-stu-id="096d7-113">In general, the recommended approach is to sign the user in with the bot using the same identity system used to provide authentication for the tab content.</span></span> <span data-ttu-id="096d7-114">Sie können dies über die Anmeldeaktion implementieren, die sich in der Regel über einen OAuth-Fluss im Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="096d7-114">You can implement this via the sign-in action, which typically logs in the user via an OAuth flow.</span></span>

<span data-ttu-id="096d7-115">Dieser Ablauf eignet sich am besten, wenn Ihr Identitätsanbieter das OAuth 2,0-Protokoll implementiert.</span><span class="sxs-lookup"><span data-stu-id="096d7-115">This flow works best if your identity provider implements the OAuth 2.0 protocol.</span></span> <span data-ttu-id="096d7-116">Anschließend können Sie die Microsoft Teams-Benutzer-ID den Anmeldeinformationen des Benutzers aus Ihrem eigenen Identitätsdienst zuordnen.</span><span class="sxs-lookup"><span data-stu-id="096d7-116">You can then associate the Teams user ID with the user’s credentials from your own identity service.</span></span>

   ![Zuordnen von Identitäten](~/assets/images/bots/associating_contexts.png)

## <a name="constructing-deep-links-to-tabs-in-messages-from-your-bot"></a><span data-ttu-id="096d7-118">Erstellen von Deep-Links zu Registerkarten in Nachrichten von Ihrem bot</span><span class="sxs-lookup"><span data-stu-id="096d7-118">Constructing deep links to tabs in messages from your bot</span></span>

<span data-ttu-id="096d7-119">Möglicherweise möchten Sie Registerkarten verwenden, um mehr Inhalte anzuzeigen, als in eine Karte passt, oder um komplexe Aufgaben zum Ausfüllen von Formularen mithilfe des Registerkartenbereichs abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="096d7-119">You may want to use tabs to show more content than can fit inside of a card, or provide a way to complete complex form-filling tasks using the tab canvas.</span></span> <span data-ttu-id="096d7-120">Beispielsweise sollten Sie den Benutzer zur Registerkarte navigieren, wenn er von Ihrem bot auf die Karte klickt.</span><span class="sxs-lookup"><span data-stu-id="096d7-120">For example, consider navigating the user to the tab when he or she clicks on the card from your bot.</span></span> <span data-ttu-id="096d7-121">Damit dies geschieht, müssen Sie die Nachricht Ihres bot codieren, um eine [Deep Link](~/concepts/build-and-test/deep-links.md) -URL zu verwenden, entweder über Markup oder als Ziel der openUrl-Aktion.</span><span class="sxs-lookup"><span data-stu-id="096d7-121">For this to happen, you’ll need to encode your bot’s message to include a [deep link](~/concepts/build-and-test/deep-links.md) URL, either via markup or as the target of the openUrl action.</span></span>

<span data-ttu-id="096d7-122">Deep-Links basieren auf einer Entitäts-Nr, bei der es sich um einen nicht transparenten Wert handelt, der einer eindeutigen Entität in Ihrem System zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="096d7-122">Deep links rely on an entityId, which is an opaque value that maps to a unique entity in your system.</span></span> <span data-ttu-id="096d7-123">Wenn die Registerkarte erstellt wird, speichern Sie im Idealfall einen einfachen Zustand (beispielsweise "Flag") im Back-End, der angibt, dass die Registerkarte im Kanal erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="096d7-123">When the tab is created, you ideally store some simple state (e.g. flag) on your backend indicating the tab has been created in the channel.</span></span> <span data-ttu-id="096d7-124">Wenn Ihr bot eine Nachricht erstellt, kann Sie auf die Entitäts-Nr, die dieser Registerkarte zugeordnet ist, abzielen.</span><span class="sxs-lookup"><span data-stu-id="096d7-124">When your bot constructs a message, it can target the entityId associated with that tab.</span></span>

<span data-ttu-id="096d7-125">**Hinweis:** in persönlichen Chats, da Registerkarten "statisch" sind und mit der APP installiert werden, können Sie immer ihre Existenz übernehmen und so tiefe Verknüpfungen entsprechend erstellen.</span><span class="sxs-lookup"><span data-stu-id="096d7-125">**Note:** in personal chats, because tabs are “static” and installed with the app, you can always assume their existence and thus construct deep links accordingly.</span></span>

## <a name="sending-notifications-for-tab-updates"></a><span data-ttu-id="096d7-126">Senden von Benachrichtigungen für Registerkarten Aktualisierungen</span><span class="sxs-lookup"><span data-stu-id="096d7-126">Sending notifications for tab updates</span></span>

<span data-ttu-id="096d7-127">Häufig möchten Sie den Endbenutzer Benachrichtigen, wenn eine Aktualisierung oder eine Benutzeraktion auf einer Registerkarte erfolgt. Ein Beispielszenario ist das Zuweisen einer Aufgabe oder eines Tickets zu einem Teammitglied und das anschließende Benachrichtigen dieses Teammitglieds.</span><span class="sxs-lookup"><span data-stu-id="096d7-127">Often you’ll want to notify the end user whenever an update or a user action occurs in a tab. An example scenario is assigning a task or ticket to a fellow team member and then notifying that team member.</span></span>

<span data-ttu-id="096d7-128">Es gibt zwei Möglichkeiten, dieses Szenario zu erreichen:</span><span class="sxs-lookup"><span data-stu-id="096d7-128">There are two ways of achieving this scenario:</span></span>

1. <span data-ttu-id="096d7-129">Wenn Sie einen ganzen Kanal benachrichtigen möchten, kann Ihr bot asynchron eine Nachricht an den Kanal senden.</span><span class="sxs-lookup"><span data-stu-id="096d7-129">If you wish to notify an entire channel your bot can asynchronously post a message to the channel.</span></span> <span data-ttu-id="096d7-130">Es gibt keine Möglichkeit für einen bot, proaktiv die Registerkarten Unterhaltung zu erstellen, wenn er nicht mit der Registerkarte erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="096d7-130">There is no way for a bot to proactively create the tab conversation if it wasn't created with the tab.</span></span>

2. <span data-ttu-id="096d7-131">Wenn Sie nur den Empfänger oder interessierte Parteien benachrichtigen möchten, die an der Aktion beteiligt sind, kann Ihr bot eine persönliche Chatnachricht an den Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="096d7-131">If you wish to only notify the recipient or interested parties involved with the action, your bot can send a personal chat message to the user.</span></span> <span data-ttu-id="096d7-132">Überprüfen Sie zunächst, ob eine persönliche Unterhaltung zwischen Ihrem bot und dem Benutzer vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="096d7-132">You should first check to see if a personal conversation between your bot and the user exists.</span></span> <span data-ttu-id="096d7-133">Wenn dies nicht der Fall ist `CreateConversation` , können Sie zum Initiieren des persönlichen Chats aufrufen.</span><span class="sxs-lookup"><span data-stu-id="096d7-133">If not, you can call `CreateConversation` to initiate the personal chat.</span></span>

<span data-ttu-id="096d7-134">Verwenden Sie in beiden Fällen Ereignisbenachrichtigungen mit Bedacht und niemals Spam für den Benutzer mit unnötigen Updates.</span><span class="sxs-lookup"><span data-stu-id="096d7-134">In both cases, use event notifications wisely and never spam the user with unnecessary updates.</span></span>