---
title: Bots in Microsoft Teams
author: surbhigupta
description: Eine Übersicht über Bots in Microsoft Teams.
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 655684ef4f2a93d3f9c3858e3bf5a84eab4bd43c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068969"
---
# <a name="bots-in-microsoft-teams"></a><span data-ttu-id="5d0f7-103">Bots in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5d0f7-103">Bots in Microsoft Teams</span></span>

<span data-ttu-id="5d0f7-104">Ein Bot, der auch als Chatbot oder Unterhaltungsbot bezeichnet wird, ist eine App, die einfache und wiederholte automatisierte Aufgaben ausführt, die von den Benutzern ausgeführt werden, z. B. Kundendienst- oder Supportmitarbeiter.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-104">A bot also referred to as a chatbot or conversational bot is an app that runs simple and repetitive automated tasks performed by the users, such as customer service or support staff.</span></span> <span data-ttu-id="5d0f7-105">Beispiele für Bots im täglichen Gebrauch sind Bots, die Informationen über das Wetter bereitstellen, Reservierungen vornehmen oder Reiseinformationen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-105">Examples of bots in everyday use include, bots that provide information about the weather, make dinner reservations, or provide travel information.</span></span> <span data-ttu-id="5d0f7-106">Eine Bot-Interaktion kann eine schnelle Frage und Antwort sein oder eine komplexe Unterhaltung, die Zugriff auf Dienste bietet.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-106">A bot interaction can be a quick question and answer, or it can be a complex conversation that provides access to services.</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/zSIysk0yL0Q]

<span data-ttu-id="5d0f7-107">Unterhaltungsbots ermöglichen Benutzern, mit Ihrem Webdienst über Text, interaktive Karten und Aufgabenmodule zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-107">Conversational bots allow users to interact with your web service through text, interactive cards, and task modules.</span></span>

![Aufrufen eines Bots mithilfe von Text](~/assets/images/invokebotwithtext.png)

![Aufrufen eines Bots mithilfe einer Karte](~/assets/images/invokebotwithcard.png)

<img src="~/assets/images/task-module-example.png" alt="Invoke bot using task module" width="400"/>

<span data-ttu-id="5d0f7-110">Unterhaltungs-Bots sind unglaublich flexibel und können so ausgelegt werden, dass sie einige einfache Befehle oder komplexe, von künstlicher Intelligenz unterstützte Und Verarbeitungsaufgaben in natürlicher Sprache verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-110">Conversational bots are incredibly flexible and can be scoped to handle a few simple commands, or complex, artificial-intelligence-powered, and natural-language-processing tasks.</span></span> <span data-ttu-id="5d0f7-111">Sie können ein Aspekt einer größeren Anwendung oder vollständig eigenständig sein.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-111">They can be one aspect of a larger application, or be completely stand-alone.</span></span>

<span data-ttu-id="5d0f7-112">Die richtige Mischung aus Karten, Text und Aufgabenmodulen zu finden, ist der Schlüssel zum Erstellen eines nützlichen Bots.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-112">Finding the right mix of cards, text, and task modules are key to create a useful bot.</span></span> <span data-ttu-id="5d0f7-113">Die folgende Abbildung zeigt einen Benutzer, der sich mit einem Bot in einem 1:1-Chat mit textbasierten und interaktiven Karten unterhält:</span><span class="sxs-lookup"><span data-stu-id="5d0f7-113">The following image shows a user conversing with a bot in a one-to-one chat using both, text and interactive cards:</span></span>

:::image type="content" source="~/assets/images/FAQPlusEndUser.gif" alt-text="Beispiel für häufig gestellte Fragen (FAQ)-Bot" border="true":::

<span data-ttu-id="5d0f7-115">Jede Interaktion zwischen dem Benutzer und dem Bot wird als Aktivität dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-115">Every interaction between the user and the bot is represented as an activity.</span></span> <span data-ttu-id="5d0f7-116">Wenn ein Bot eine Aktivität empfängt, übergibt er sie an seine Aktivitätshandler.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-116">When a bot receives an activity, it passes it on to its activity handlers.</span></span> <span data-ttu-id="5d0f7-117">Weitere Informationen finden Sie unter [Bot-Aktivitätshandler.](~/bots/bot-basics.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-117">For more information, see [bot activity handlers](~/bots/bot-basics.md).</span></span> 

<span data-ttu-id="5d0f7-118">Darüber hinaus sind Bots Apps, die über eine Unterhaltungsoberfläche verfügen.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-118">In addition, bots are apps that have a conversational interface.</span></span> <span data-ttu-id="5d0f7-119">Sie können mit einem Bot mit Text, interaktiven Karten und Sprache interagieren.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-119">You can interact with a bot using text, interactive cards, and speech.</span></span> <span data-ttu-id="5d0f7-120">Ein Bot verhält sich anders, je nachdem, ob es sich bei der Unterhaltung um eine Kanal- oder Gruppenchatunterhaltung oder um eine 1:1-Unterhaltung handelt.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-120">A bot behaves differently depending on whether the conversation is a channel or group chat conversation, or it is a one-to-one conversation.</span></span> <span data-ttu-id="5d0f7-121">Unterhaltungen werden über den Bot Framework-Connector verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-121">Conversations are handled through the Bot Framework connector.</span></span> <span data-ttu-id="5d0f7-122">Weitere Informationen finden Sie unter [Unterhaltungsgrundlagen.](~/bots/how-to/conversations/conversation-basics.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-122">For more information, see [conversation basics](~/bots/how-to/conversations/conversation-basics.md).</span></span>

<span data-ttu-id="5d0f7-123">Ihr Bot erfordert Kontextinformationen, z. B. Benutzerprofildetails, um auf relevante Inhalte zuzugreifen und die Bot-Erfahrung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-123">Your bot requires contextual information, such as user profile details to access relevant content and enhance the bot experience.</span></span> <span data-ttu-id="5d0f7-124">Weitere Informationen finden Sie unter [abrufen Teams Kontext.](~/bots/how-to/get-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-124">For more information, see [get Teams context](~/bots/how-to/get-teams-context.md).</span></span> 

<span data-ttu-id="5d0f7-125">Sie können Dateien auch über den Bot senden und empfangen, indem Sie Graph-APIs oder Teams-Bot-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-125">You can also send and receive files through the bot using Graph APIs or Teams bot APIs.</span></span> <span data-ttu-id="5d0f7-126">Weitere Informationen finden Sie unter [Senden und Empfangen von Dateien über den Bot.](~/bots/how-to/bots-filesv4.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-126">For more information, see [send and receive files through the bot](~/bots/how-to/bots-filesv4.md).</span></span>

<span data-ttu-id="5d0f7-127">Darüber hinaus wird die Ratenbegrenzung verwendet, um Bots zu optimieren, die für Ihre Teams-Anwendung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-127">In addition, rate limiting is used to optimize bots used for your Teams application.</span></span> <span data-ttu-id="5d0f7-128">Um Microsoft Teams und seine Benutzer zu schützen, bieten die Bot-APIs ein Preislimit für eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-128">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="5d0f7-129">Weitere Informationen finden Sie unter [Optimieren Ihres Bots mit Einer Begrenzung der Rate in Teams.](~/bots/how-to/rate-limit.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-129">For more information, see [optimize your bot with rate limiting in Teams](~/bots/how-to/rate-limit.md).</span></span>

<span data-ttu-id="5d0f7-130">Mit Microsoft Graph-APIs für Anrufe und Onlinebesprechungen können Microsoft Teams Apps jetzt per Sprach- und Videofunktion mit Benutzern interagieren.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-130">With Microsoft Graph APIs for calls and online meetings, Microsoft Teams apps can now interact with users using voice and video.</span></span> <span data-ttu-id="5d0f7-131">Weitere Informationen finden Sie unter ["Bots für Anrufe und Besprechungen".](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-131">For more information, see [calls and meetings bots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md).</span></span> 

<span data-ttu-id="5d0f7-132">Sie können die Teams-Bot-APIs verwenden, um Informationen für ein oder mehrere Mitglieder eines Chats oder Teams abzurufen.</span><span class="sxs-lookup"><span data-stu-id="5d0f7-132">You can use the Teams bot APIs to get information for one or more members of a chat or team.</span></span> <span data-ttu-id="5d0f7-133">Weitere Informationen finden Sie unter [Änderungen an Teams Bot-APIs zum Abrufen von Team- oder Chatmitgliedern.](~/resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="5d0f7-133">For more information, see [changes to Teams bot APIs for fetching team or chat members](~/resources/team-chat-member-api-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d0f7-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5d0f7-134">See also</span></span>

[<span data-ttu-id="5d0f7-135">Erstellen eines Bots für Teams</span><span class="sxs-lookup"><span data-stu-id="5d0f7-135">Create a bot for Teams</span></span>](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="next-step"></a><span data-ttu-id="5d0f7-136">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="5d0f7-136">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d0f7-137">Tools und SDKs</span><span class="sxs-lookup"><span data-stu-id="5d0f7-137">Bots and SDKs</span></span>](~/bots/bot-features.md)
