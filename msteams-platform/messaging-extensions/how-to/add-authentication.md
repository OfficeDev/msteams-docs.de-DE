---
title: Hinzufügen von Authentifizierung zu Ihrer Messaging Erweiterung
author: clearab
description: Hinzufügen einer Authentifizierung zu einer Messaging Erweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f7ebbcd99b1ec35900de7ec2f54f93263918e945
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674145"
---
# <a name="add-authentication-to-your-messaging-extension"></a><span data-ttu-id="18289-103">Hinzufügen von Authentifizierung zu Ihrer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="18289-103">Add authentication to your messaging extension</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a><span data-ttu-id="18289-104">Identifizieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="18289-104">Identify the user</span></span>

<span data-ttu-id="18289-105">Jede Anforderung an ihre Dienste umfasst die verborgene ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="18289-105">Every request to your services includes the obfuscated ID of the user that performed the request, as well as the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="18289-106">Die `id` Werte `aadObjectId` und sind garantiert die des authentifizierten Teams-Benutzers.</span><span class="sxs-lookup"><span data-stu-id="18289-106">The `id` and `aadObjectId` values are guaranteed to be that of the authenticated Teams user.</span></span> <span data-ttu-id="18289-107">Sie können als Schlüssel zum Nachschlagen von Anmeldeinformationen oder einem beliebigen zwischengespeicherten Zustand in Ihrem Dienst verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="18289-107">They can be used as keys to look up credentials or any cached state in your service.</span></span> <span data-ttu-id="18289-108">Darüber hinaus enthält jede Anforderung die Azure Active Directory Mandanten-ID des Benutzers, die zum Identifizieren der Organisation des Benutzers verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="18289-108">In addition, each request contains the Azure Active Directory tenant ID of the user, which can be used to identify the user’s organization.</span></span> <span data-ttu-id="18289-109">Wenn zutreffend, enthält die Anforderung auch die Team-und Kanal-IDs, aus denen die Anforderung stammt.</span><span class="sxs-lookup"><span data-stu-id="18289-109">If applicable, the request also contains the team and channel IDs from which the request originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="18289-110">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="18289-110">Authentication</span></span>

<span data-ttu-id="18289-111">Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messaging Erweiterung verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="18289-111">If your service requires user authentication, you need to sign in the user before he or she can use the messaging extension.</span></span> <span data-ttu-id="18289-112">Wenn Sie einen bot oder eine Registerkarte geschrieben haben, die den Benutzer signiert, sollte dieser Abschnitt vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="18289-112">If you have written a bot or a tab that signs in the user, this section should be familiar.</span></span>

<span data-ttu-id="18289-113">Die Sequenz lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="18289-113">The sequence is as follows:</span></span>

1. <span data-ttu-id="18289-114">Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an den Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="18289-114">User issues a query, or the default query is automatically sent to your service.</span></span>
2. <span data-ttu-id="18289-115">Der Dienst überprüft, ob der Benutzer zuerst authentifiziert wurde, indem er die Benutzer-ID des Teams überprüft.</span><span class="sxs-lookup"><span data-stu-id="18289-115">Your service checks whether the user has first authenticated by inspecting the Teams user ID.</span></span>
3. <span data-ttu-id="18289-116">Wenn der Benutzer nicht authentifiziert wurde, senden Sie eine `auth` Antwort mit einer `openUrl` vorgeschlagenen Aktion einschließlich der Authentifizierungs-URL zurück.</span><span class="sxs-lookup"><span data-stu-id="18289-116">If the user has not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
4. <span data-ttu-id="18289-117">Der Microsoft Teams-Client startet ein Popupfenster, das Ihre Webseite unter Verwendung der angegebenen Authentifizierungs-URL hostet.</span><span class="sxs-lookup"><span data-stu-id="18289-117">The Microsoft Teams client launches a pop-up window hosting your webpage using the given authentication URL.</span></span>
5. <span data-ttu-id="18289-118">Nachdem sich der Benutzer angemeldet hat, sollten Sie das Fenster schließen und einen "Authentifizierungscode" an den Microsoft Teams-Client senden.</span><span class="sxs-lookup"><span data-stu-id="18289-118">After the user signs in, you should close your window and send an "authentication code" to the Teams client.</span></span>
6. <span data-ttu-id="18289-119">Der Microsoft Teams-Client gibt dann die Abfrage erneut an Ihren Dienst aus, der den in Schritt 5 übergebenen Authentifizierungscode enthält.</span><span class="sxs-lookup"><span data-stu-id="18289-119">The Teams client then reissues the query to your service, which includes the authentication code passed in step 5.</span></span>

<span data-ttu-id="18289-120">Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem in Schritt 5 übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="18289-120">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="18289-121">Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmelde Ablauf vorzutäuschen oder zu gefährden.</span><span class="sxs-lookup"><span data-stu-id="18289-121">This ensures that a malicious user does not try to spoof or compromise the sign-in flow.</span></span> <span data-ttu-id="18289-122">Dies effektiv "schließt die Schleife", um die sichere Authentifizierungssequenz abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="18289-122">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="18289-123">Reagieren mit einer Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="18289-123">Respond with a sign-in action</span></span>

<span data-ttu-id="18289-124">Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, Antworten Sie mit einer vorgeschlagenen Aktion `openUrl` vom Typ, die die Authentifizierungs-URL enthält.</span><span class="sxs-lookup"><span data-stu-id="18289-124">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="18289-125">Antwortbeispiel für eine Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="18289-125">Response example for a sign-in action</span></span>

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
> <span data-ttu-id="18289-126">Damit die Anmelde Umgebung in einem Teams-Popup gehostet werden kann, muss der Domänenteil der URL in der Liste der gültigen Domänen in Ihrer APP aufgeführt sein.</span><span class="sxs-lookup"><span data-stu-id="18289-126">For the sign-in experience to be hosted in a Teams pop-up, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="18289-127">(Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifest-Schema.)</span><span class="sxs-lookup"><span data-stu-id="18289-127">(See [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.)</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="18289-128">Starten des Anmelde Flusses</span><span class="sxs-lookup"><span data-stu-id="18289-128">Start the sign-in flow</span></span>

<span data-ttu-id="18289-129">Ihre Anmelde Erfahrung sollte reagieren und in ein Popupfenster passt.</span><span class="sxs-lookup"><span data-stu-id="18289-129">Your sign-in experience should be responsive and fit within a popup window.</span></span> <span data-ttu-id="18289-130">Sie sollte in das [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübergabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="18289-130">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="18289-131">Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams durchführen, muss der Code im Fenster zuerst `microsoftTeams.initialize()`aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="18289-131">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="18289-132">Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Benutzer-ID des Teams an das Fenster übergeben, das dann an die OAuth-Anmelde-URL übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="18289-132">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then can pass it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="18289-133">Abschließen des Anmelde Flusses</span><span class="sxs-lookup"><span data-stu-id="18289-133">Complete the sign-in flow</span></span>

<span data-ttu-id="18289-134">Wenn die Anmeldeanforderung abgeschlossen wird und zu Ihrer Seite zurückgeleitet wird, sollten Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="18289-134">When the sign-in request completes and redirects back to your page, it should perform the following steps:</span></span>

1. <span data-ttu-id="18289-135">Generieren Sie einen Sicherheitscode.</span><span class="sxs-lookup"><span data-stu-id="18289-135">Generate a security code.</span></span> <span data-ttu-id="18289-136">(Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst Zwischenspeichern, zusammen mit den Anmeldeinformationen, die über den Anmelde Fluss abgerufen werden (beispielsweise OAuth 2,0-Token).</span><span class="sxs-lookup"><span data-stu-id="18289-136">(This can be a random number.) You need to cache this code on your service, along with the credentials obtained through the sign-in flow (such as OAuth 2.0 tokens).</span></span>
2. <span data-ttu-id="18289-137">Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode an, und übergeben Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="18289-137">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="18289-138">Zu diesem Zeitpunkt wird das Fenster geschlossen, und die Steuerung wird an den Microsoft Teams-Client übergeben.</span><span class="sxs-lookup"><span data-stu-id="18289-138">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="18289-139">Der Client kann jetzt die ursprüngliche Benutzerabfrage erneut ausgeben, zusammen mit dem Sicherheitscode in der `state` -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="18289-139">The client now can reissue the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="18289-140">Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="18289-140">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="18289-141">Beispiel für eine erneut aufgegebene Anforderung</span><span class="sxs-lookup"><span data-stu-id="18289-141">Reissued request example</span></span>

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

