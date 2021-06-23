---
title: Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung
author: surbhigupta
description: So fügen Sie einer Messaging-Erweiterung eine Authentifizierung hinzu
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: d1ebde822e1a0216edaa1b85ac6142234ae34b78
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068924"
---
# <a name="add-authentication-to-your-messaging-extension"></a><span data-ttu-id="3794e-103">Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="3794e-103">Add authentication to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a><span data-ttu-id="3794e-104">Identifizieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="3794e-104">Identify the user</span></span>

<span data-ttu-id="3794e-105">Jede Anforderung an Ihre Dienste enthält die Benutzer-ID, den Anzeigenamen des Benutzers und Azure Active Directory Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="3794e-105">Every request to your services includes the user  ID, the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="3794e-106">Die `id` und die Werte sind für den `aadObjectId` authentifizierten Teams Benutzer garantiert.</span><span class="sxs-lookup"><span data-stu-id="3794e-106">The `id` and `aadObjectId` values are guaranteed for the authenticated Teams user.</span></span> <span data-ttu-id="3794e-107">Sie werden als Schlüssel verwendet, um die Anmeldeinformationen oder einen zwischengespeicherten Status in Ihrem Dienst nachzuschlagen.</span><span class="sxs-lookup"><span data-stu-id="3794e-107">They are used as keys to look up the credentials or any cached state in your service.</span></span> <span data-ttu-id="3794e-108">Darüber hinaus enthält jede Anforderung die Azure Active Directory Mandanten-ID des Benutzers, die verwendet wird, um die Organisation des Benutzers zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="3794e-108">In addition, each request contains the Azure Active Directory tenant ID of the user, which is used to identify the user’s organization.</span></span> <span data-ttu-id="3794e-109">Falls zutreffend, enthält die Anforderung auch die Team-ID und kanal-ID, von der die Anforderung stammt.</span><span class="sxs-lookup"><span data-stu-id="3794e-109">If applicable, the request also contains the team Id and channel ID from which the request is originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="3794e-110">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="3794e-110">Authentication</span></span>

<span data-ttu-id="3794e-111">Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen sich die Benutzer anmelden, bevor sie die Messaging-Erweiterung verwenden.</span><span class="sxs-lookup"><span data-stu-id="3794e-111">If your service requires user authentication, the users must sign in before they use the messaging extension.</span></span> <span data-ttu-id="3794e-112">Die Authentifizierungsschritte ähneln denen eines Bots oder einer Registerkarte. Die Sequenz sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="3794e-112">The authentication steps are similar to that of a bot or tab. The sequence is as follows:</span></span>

1. <span data-ttu-id="3794e-113">Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="3794e-113">User issues a query, or the default query is automatically sent to your service.</span></span>
1. <span data-ttu-id="3794e-114">Ihr Dienst überprüft anhand der Teams Benutzer-ID, ob der Benutzer authentifiziert ist.</span><span class="sxs-lookup"><span data-stu-id="3794e-114">Your service checks whether the user is authenticated by inspecting the Teams user ID.</span></span>
1. <span data-ttu-id="3794e-115">Wenn der Benutzer nicht authentifiziert ist, senden Sie eine `auth` Antwort mit einer vorgeschlagenen Aktion einschließlich der `openUrl` Authentifizierungs-URL zurück.</span><span class="sxs-lookup"><span data-stu-id="3794e-115">If the user is not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
1. <span data-ttu-id="3794e-116">Der Microsoft Teams-Client startet ein Dialogfeld, in dem Ihre Webseite mithilfe der angegebenen Authentifizierungs-URL gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="3794e-116">The Microsoft Teams client launches a dialog box hosting your webpage using the given authentication URL.</span></span>
1. <span data-ttu-id="3794e-117">Nachdem sich der Benutzer angemeldet hat, sollten Sie das Fenster schließen und einen **Authentifizierungscode** an den Teams Client senden.</span><span class="sxs-lookup"><span data-stu-id="3794e-117">After the user signs in, you should close your window and send an **authentication code** to the Teams client.</span></span>
1. <span data-ttu-id="3794e-118">Der Teams-Client sendet dann die Abfrage erneut an Ihren Dienst, der den in Schritt 5 übergebenen Authentifizierungscode enthält.</span><span class="sxs-lookup"><span data-stu-id="3794e-118">The Teams client then reissues the query to your service, which includes the authentication code passed in Step 5.</span></span>

<span data-ttu-id="3794e-119">Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="3794e-119">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="3794e-120">Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu kompromittieren.</span><span class="sxs-lookup"><span data-stu-id="3794e-120">This ensures that a malicious user does not try to spoof or compromise the sign in flow.</span></span> <span data-ttu-id="3794e-121">Dadurch wird die Schleife "geschlossen", um die sichere Authentifizierungssequenz abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="3794e-121">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="3794e-122">Antworten mit einer Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="3794e-122">Respond with a sign-in action</span></span>

<span data-ttu-id="3794e-123">Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, antworten Sie mit einer vorgeschlagenen Aktion vom `openUrl` Typ, die die Authentifizierungs-URL enthält.</span><span class="sxs-lookup"><span data-stu-id="3794e-123">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="3794e-124">Antwortbeispiel für eine Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="3794e-124">Response example for a sign-in action</span></span>

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
> <span data-ttu-id="3794e-125">Damit die Anmeldeumgebung in einem Teams Popupfenster gehostet werden kann, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden.</span><span class="sxs-lookup"><span data-stu-id="3794e-125">For the sign in experience to be hosted in a Teams pop-up window, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="3794e-126">Weitere Informationen finden Sie unter ["validDomains"](~/resources/schema/manifest-schema.md#validdomains) im Manifestschema.</span><span class="sxs-lookup"><span data-stu-id="3794e-126">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="3794e-127">Starten des Anmeldeflusses</span><span class="sxs-lookup"><span data-stu-id="3794e-127">Start the sign in flow</span></span>

<span data-ttu-id="3794e-128">Die Anmeldeerfahrung muss reaktionsfähig sein und in ein Popupfenster passen.</span><span class="sxs-lookup"><span data-stu-id="3794e-128">Your sign in experience must be responsive and fit within a pop-up window.</span></span> <span data-ttu-id="3794e-129">Sie sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübergabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="3794e-129">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="3794e-130">Wie bei anderen eingebetteten Oberflächen, die in Microsoft Teams ausgeführt werden, muss Ihr Code innerhalb des Fensters zuerst aufgerufen `microsoftTeams.initialize()` werden.</span><span class="sxs-lookup"><span data-stu-id="3794e-130">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="3794e-131">Wenn Ihr Code einen OAuth-Fluss durchführt, können Sie die Teams Benutzer-ID an Ihr Fenster übergeben, das sie dann an die OAuth-Anmelde-URL übergibt.</span><span class="sxs-lookup"><span data-stu-id="3794e-131">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then passes it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="3794e-132">Abschließen des Anmeldeflusses</span><span class="sxs-lookup"><span data-stu-id="3794e-132">Complete the sign in flow</span></span>

<span data-ttu-id="3794e-133">Wenn die Anmeldeanforderung abgeschlossen ist und zurück zu Ihrer Seite geleitet wird, müssen die folgenden Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="3794e-133">When the sign in request completes and redirects back to your page, it must perform the following steps:</span></span>

1. <span data-ttu-id="3794e-134">Generieren Sie einen Sicherheitscode.</span><span class="sxs-lookup"><span data-stu-id="3794e-134">Generate a security code.</span></span> <span data-ttu-id="3794e-135">Dies ist eine Zufallszahl.</span><span class="sxs-lookup"><span data-stu-id="3794e-135">This is a random number.</span></span> <span data-ttu-id="3794e-136">Sie müssen diesen Code zusammen mit den über den Anmeldefluss abgerufenen Anmeldeinformationen, z. B. OAuth 2.0-Token, in Ihrem Dienst zwischenspeichern.</span><span class="sxs-lookup"><span data-stu-id="3794e-136">You must cache this code on your service, along with the credentials obtained through the sign in flow, such as OAuth 2.0 tokens.</span></span>
1. <span data-ttu-id="3794e-137">Rufen Sie `microsoftTeams.authentication.notifySuccess` den Sicherheitscode auf, und übergeben Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="3794e-137">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="3794e-138">An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams Client übergeben.</span><span class="sxs-lookup"><span data-stu-id="3794e-138">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="3794e-139">Der Client stellt jetzt die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der Eigenschaft neu `state` dar.</span><span class="sxs-lookup"><span data-stu-id="3794e-139">The client now reissues the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="3794e-140">Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="3794e-140">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="3794e-141">Beispiel für erneutesued-Anforderung</span><span class="sxs-lookup"><span data-stu-id="3794e-141">Reissued request example</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="3794e-142">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="3794e-142">Code sample</span></span>
|<span data-ttu-id="3794e-143">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="3794e-143">**Sample name**</span></span> | <span data-ttu-id="3794e-144">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="3794e-144">**Description**</span></span> |<span data-ttu-id="3794e-145">**.NET**</span><span class="sxs-lookup"><span data-stu-id="3794e-145">**.NET**</span></span> | <span data-ttu-id="3794e-146">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="3794e-146">**Node.js**</span></span>|
|----------------|-----------------|--------------|----------------|
|<span data-ttu-id="3794e-147">Messaging-Erweiterungen – Authentifizierung und Konfiguration</span><span class="sxs-lookup"><span data-stu-id="3794e-147">Messaging extensions - auth and config</span></span> | <span data-ttu-id="3794e-148">Eine Messaging-Erweiterung, die über eine Konfigurationsseite verfügt, Suchanforderungen akzeptiert und Ergebnisse zurückgibt, nachdem sich der Benutzer angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="3794e-148">A Messaging Extension that has a configuration page, accepts search requests, and returns results after the user has signed in.</span></span> |[<span data-ttu-id="3794e-149">View</span><span class="sxs-lookup"><span data-stu-id="3794e-149">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[<span data-ttu-id="3794e-150">View</span><span class="sxs-lookup"><span data-stu-id="3794e-150">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)| 

 
