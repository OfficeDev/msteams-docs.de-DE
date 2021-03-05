---
title: Hinzufügen der Authentifizierung zu Ihrer Messagingerweiterung
author: clearab
description: Hinzufügen der Authentifizierung zu einer Messagingerweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: d673f52e63ba845675f6631470af68d65c7297ad
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449570"
---
# <a name="add-authentication-to-your-messaging-extension"></a><span data-ttu-id="8b4d1-103">Hinzufügen der Authentifizierung zu Ihrer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="8b4d1-103">Add authentication to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a><span data-ttu-id="8b4d1-104">Identifizieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="8b4d1-104">Identify the user</span></span>

<span data-ttu-id="8b4d1-105">Jede Anforderung an Ihre Dienste enthält die verschleierte ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory-Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-105">Every request to your services includes the obfuscated ID of the user that performed the request, as well as the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="8b4d1-106">Die `id` Werte und sind garantiert der des `aadObjectId` authentifizierten Teams-Benutzers.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-106">The `id` and `aadObjectId` values are guaranteed to be that of the authenticated Teams user.</span></span> <span data-ttu-id="8b4d1-107">Sie können als Schlüssel verwendet werden, um Anmeldeinformationen oder einen beliebigen zwischengespeicherten Status in Ihrem Dienst nach zu suchen.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-107">They can be used as keys to look up credentials or any cached state in your service.</span></span> <span data-ttu-id="8b4d1-108">Darüber hinaus enthält jede Anforderung die Azure Active Directory-Mandanten-ID des Benutzers, mit der die Organisation des Benutzers identifiziert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-108">In addition, each request contains the Azure Active Directory tenant ID of the user, which can be used to identify the user’s organization.</span></span> <span data-ttu-id="8b4d1-109">Falls zutreffend, enthält die Anforderung auch die Team- und Kanal-IDs, von denen die Anforderung stammt.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-109">If applicable, the request also contains the team and channel IDs from which the request originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="8b4d1-110">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="8b4d1-110">Authentication</span></span>

<span data-ttu-id="8b4d1-111">Wenn ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messagingerweiterung verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-111">If your service requires user authentication, you need to sign in the user before he or she can use the messaging extension.</span></span> <span data-ttu-id="8b4d1-112">Wenn Sie einen Bot oder eine Registerkarte geschrieben haben, die sich im Benutzer signiert, sollte dieser Abschnitt vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-112">If you have written a bot or a tab that signs in the user, this section should be familiar.</span></span>

<span data-ttu-id="8b4d1-113">Die Reihenfolge lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8b4d1-113">The sequence is as follows:</span></span>

1. <span data-ttu-id="8b4d1-114">Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-114">User issues a query, or the default query is automatically sent to your service.</span></span>
2. <span data-ttu-id="8b4d1-115">Ihr Dienst überprüft, ob sich der Benutzer zuerst authentifiziert hat, indem er die Teams-Benutzer-ID überprüft.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-115">Your service checks whether the user has first authenticated by inspecting the Teams user ID.</span></span>
3. <span data-ttu-id="8b4d1-116">Wenn sich der Benutzer nicht authentifiziert hat, senden Sie eine Antwort mit einer vorgeschlagenen `auth` `openUrl` Aktion zurück, einschließlich der Authentifizierungs-URL.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-116">If the user has not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
4. <span data-ttu-id="8b4d1-117">Der Microsoft Teams-Client startet ein Popupfenster, in dem Ihre Webseite mit der angegebenen Authentifizierungs-URL hosten wird.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-117">The Microsoft Teams client launches a pop-up window hosting your webpage using the given authentication URL.</span></span>
5. <span data-ttu-id="8b4d1-118">Nach der Anmeldung des Benutzers sollten Sie ihr Fenster schließen und einen "Authentifizierungscode" an den Teams-Client senden.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-118">After the user signs in, you should close your window and send an "authentication code" to the Teams client.</span></span>
6. <span data-ttu-id="8b4d1-119">Der Teams-Client gibt die Abfrage dann erneut an Ihren Dienst weiter, der den in Schritt 5 übergebenen Authentifizierungscode enthält.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-119">The Teams client then reissues the query to your service, which includes the authentication code passed in step 5.</span></span>

<span data-ttu-id="8b4d1-120">Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 entspricht.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-120">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="8b4d1-121">Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu schädlich zu machen.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-121">This ensures that a malicious user does not try to spoof or compromise the sign-in flow.</span></span> <span data-ttu-id="8b4d1-122">Dadurch wird die Schleife geschlossen, um die sichere Authentifizierungssequenz zu beenden.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-122">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="8b4d1-123">Reagieren mit einer Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="8b4d1-123">Respond with a sign-in action</span></span>

<span data-ttu-id="8b4d1-124">Um einen nicht authentifizierten Benutzer zur Anmeldung auffordert, antworten Sie mit einer vorgeschlagenen Aktion vom Typ, die `openUrl` die Authentifizierungs-URL enthält.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-124">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="8b4d1-125">Antwortbeispiel für eine Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="8b4d1-125">Response example for a sign-in action</span></span>

```json
{
  "composeExtension":{
    "type":"auth",
    "suggestedActions":{
      "actions":[
        {
          "type": "openUrl",
          "value": "https://example.com/auth",
          "title": "Sign in to this app"
        }
      ]
    }
  }
}
```

> [!NOTE]
> <span data-ttu-id="8b4d1-126">Damit die Anmeldeerfahrung in einem Teams-Popup gehostet wird, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-126">For the sign-in experience to be hosted in a Teams pop-up, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="8b4d1-127">(Siehe [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschema.)</span><span class="sxs-lookup"><span data-stu-id="8b4d1-127">(See [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.)</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="8b4d1-128">Starten des Anmeldeflusses</span><span class="sxs-lookup"><span data-stu-id="8b4d1-128">Start the sign-in flow</span></span>

<span data-ttu-id="8b4d1-129">Ihre Anmeldeerfahrung sollte reaktionsfähig sein und in ein Popupfenster passen.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-129">Your sign-in experience should be responsive and fit within a popup window.</span></span> <span data-ttu-id="8b4d1-130">Es sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübertragung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-130">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="8b4d1-131">Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams ausgeführt werden, muss Ihr Code im Fenster zuerst `microsoftTeams.initialize()` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-131">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="8b4d1-132">Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Teams-Benutzer-ID an Ihr Fenster übergeben, die sie dann an die OAuth-Anmelde-URL übergeben kann.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-132">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then can pass it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="8b4d1-133">Abschließen des Anmeldeflusses</span><span class="sxs-lookup"><span data-stu-id="8b4d1-133">Complete the sign-in flow</span></span>

<span data-ttu-id="8b4d1-134">Wenn die Anmeldeanforderung abgeschlossen ist und wieder zu Ihrer Seite umgeleitet wird, sollten sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="8b4d1-134">When the sign-in request completes and redirects back to your page, it should perform the following steps:</span></span>

1. <span data-ttu-id="8b4d1-135">Generieren Sie einen Sicherheitscode.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-135">Generate a security code.</span></span> <span data-ttu-id="8b4d1-136">(Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst zusammen mit den Anmeldeinformationen zwischenspeichern, die über den Anmeldefluss (z. B. OAuth 2.0-Token) erhalten wurden.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-136">(This can be a random number.) You need to cache this code on your service, along with the credentials obtained through the sign-in flow (such as OAuth 2.0 tokens).</span></span>
2. <span data-ttu-id="8b4d1-137">Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode auf, und übergeben Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-137">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="8b4d1-138">An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams-Client übergeben.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-138">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="8b4d1-139">Der Client kann nun die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der Eigenschaft erneut `state` ausführen.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-139">The client now can reissue the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="8b4d1-140">Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nach zu suchen, um die Authentifizierungssequenz zu vervollständigen und dann die Benutzeranforderung zu vervollständigen.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-140">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="8b4d1-141">Beispiel für neu ausgestellte Anforderung</span><span class="sxs-lookup"><span data-stu-id="8b4d1-141">Reissued request example</span></span>

```json
{
    "name": "composeExtension/query",
    "value": {
        "commandId": "insertWiki",
        "parameters": [{
            "name": "searchKeyword",
            "value": "lakers"
        }],
        "state": "12345",
        "queryOptions": {
            "skip": 0,
            "count": 25
        }
    },
    "type": "invoke",
    "timestamp": "2017-04-26T05:18:25.629Z",
    "localTimestamp": "2017-04-25T22:18:25.629-07:00",
    "entities": [{
        "locale": "en-US",
        "country": "US",
        "platform": "Web",
        "type": "clientInfo"
    }],
    "text": "",
    "attachments": [],
    "address": {
        "id": "f:7638210432489287768",
        "channelId": "msteams",
        "user": {
            "id": "29:1A5TJWHkbOwSyu_L9Ktk9QFI1d_kBOEPeNEeO1INscpKHzHTvWfiau5AX_6y3SuiOby-r73dzHJ17HipUWqGPgw",
            "aadObjectId": "fc8ca1c0-d043-4af6-b09f-141536207403"
        },
        "conversation": {
            "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
        },
        "bot": {
            "id": "28:c073afa8-7e77-4f92-b3e7-aa589e952a3e",
            "name": "maotestbot2"
        },
        "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
        "useAuth": true
    },
    "source": "msteams"
}
```

## <a name="code-sample"></a><span data-ttu-id="8b4d1-142">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="8b4d1-142">Code sample</span></span>
|<span data-ttu-id="8b4d1-143">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="8b4d1-143">**Sample name**</span></span> | <span data-ttu-id="8b4d1-144">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="8b4d1-144">**Description**</span></span> |<span data-ttu-id="8b4d1-145">**.NET**</span><span class="sxs-lookup"><span data-stu-id="8b4d1-145">**.NET**</span></span> | <span data-ttu-id="8b4d1-146">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="8b4d1-146">**Node.js**</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="8b4d1-147">Messagingerweiterungen – Authentifizierung und Konfiguration</span><span class="sxs-lookup"><span data-stu-id="8b4d1-147">Messaging extensions - auth and config</span></span> | <span data-ttu-id="8b4d1-148">Eine Messagingerweiterung mit einer Konfigurationsseite, die Suchanforderungen akzeptiert und Ergebnisse zurückgibt, nachdem sich der Benutzer angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="8b4d1-148">A Messaging Extension that has a configuration page, accepts search requests, and returns results after the user has signed in.</span></span> |[<span data-ttu-id="8b4d1-149">View</span><span class="sxs-lookup"><span data-stu-id="8b4d1-149">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[<span data-ttu-id="8b4d1-150">View</span><span class="sxs-lookup"><span data-stu-id="8b4d1-150">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)| 

 
