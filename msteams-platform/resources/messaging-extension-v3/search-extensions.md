---
title: Suche mit Messaging Erweiterungen
description: Beschreibt, wie suchbasierte Messaging Erweiterungen entwickelt werden
keywords: Microsoft Teams Messaging Extensions Messaging Extensions Search
ms.date: 05/20/2019
ms.openlocfilehash: 7baf55d7184784a436ac5a3d6b82db233389bca7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674368"
---
# <a name="search-with-messaging-extensions"></a><span data-ttu-id="df733-104">Suche mit Messaging Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="df733-104">Search with messaging extensions</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

<span data-ttu-id="df733-105">Suchbasierte Messaging-Erweiterungen ermöglichen es Ihnen, ihren Dienst abzufragen und diese Informationen in Form einer Karte nach rechts in Ihre Nachricht einzusenden.</span><span class="sxs-lookup"><span data-stu-id="df733-105">Search based messaging extensions allow you to query your service and post that information in the form of a card, right into your message</span></span>

![Beispiel für eine Messaging Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

<span data-ttu-id="df733-107">In den folgenden Abschnitten wird die Vorgehensweise beschrieben.</span><span class="sxs-lookup"><span data-stu-id="df733-107">The following sections describe how to do this.</span></span>

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a><span data-ttu-id="df733-108">Nachrichten Erweiterungen für Such Typen</span><span class="sxs-lookup"><span data-stu-id="df733-108">Search type message extensions</span></span>

<span data-ttu-id="df733-109">Legen Sie für die suchbasierte Messaging `type` Erweiterung den `query`Parameter auf fest.</span><span class="sxs-lookup"><span data-stu-id="df733-109">For search based messaging extension set the `type` parameter to `query`.</span></span> <span data-ttu-id="df733-110">Unten sehen Sie ein Beispiel für ein Manifest mit einem einzigen Suchbefehl.</span><span class="sxs-lookup"><span data-stu-id="df733-110">Below is an example of a manifest with a single search command.</span></span> <span data-ttu-id="df733-111">Einer einzelnen Messaging Erweiterung können bis zu 10 verschiedene Befehle zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="df733-111">A single messaging extension can have up to 10 different commands associated with it.</span></span> <span data-ttu-id="df733-112">Dies kann sowohl mehrere Suchfunktionen als auch mehrere Aktionsbasierte Befehle umfassen.</span><span class="sxs-lookup"><span data-stu-id="df733-112">This can include both multiple search and multiple Action-based commands.</span></span>

#### <a name="complete-app-manifest-example"></a><span data-ttu-id="df733-113">Beispiel für ein vollständiges App-Manifest</span><span class="sxs-lookup"><span data-stu-id="df733-113">Complete app manifest example</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.bing",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://bingbotservice.azurewebsites.net/",
    "privacyUrl": "http://bingbotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://bingbotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "Bing",
    "full": "Bing"
  },
  "description": {
    "short": "Find Bing search results",
    "full": "Find Bing search results and share them with your team members."
  },
  "icons": {
    "outline": "bing-outline.jpg",
    "color": "bing-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [{
          "id": "searchCmd",
          "description": "Search Bing for information on the web",
          "title": "Search",
          "initialRun": true,
          "parameters": [{
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "bingbotservice.azurewebsites.net",
    "*.bingbotservice.azurewebsites.net"
  ]
}
```

### <a name="test-via-uploading"></a><span data-ttu-id="df733-114">Testen über hochladen</span><span class="sxs-lookup"><span data-stu-id="df733-114">Test via uploading</span></span>

<span data-ttu-id="df733-115">Sie können Ihre Messaging Erweiterung testen, indem Sie Ihre APP hochladen.</span><span class="sxs-lookup"><span data-stu-id="df733-115">You can test your messaging extension by uploading your app.</span></span>

<span data-ttu-id="df733-116">Um Ihre Messaging Erweiterung zu öffnen, navigieren Sie zu einem beliebigen Chat oder Kanal.</span><span class="sxs-lookup"><span data-stu-id="df733-116">To open your messaging extension, navigate to any of your chats or channels.</span></span> <span data-ttu-id="df733-117">Wählen Sie im Feld Verfassen die Schaltfläche **Weitere Optionen** (**&#8943;**) aus, und wählen Sie Ihre Messaging Erweiterung aus.</span><span class="sxs-lookup"><span data-stu-id="df733-117">Choose the **More options** (**&#8943;**) button in the compose box, and choose your messaging extension.</span></span>

## <a name="add-event-handlers"></a><span data-ttu-id="df733-118">Hinzufügen von Ereignishandlern</span><span class="sxs-lookup"><span data-stu-id="df733-118">Add event handlers</span></span>

<span data-ttu-id="df733-119">Der Großteil ihrer Arbeit umfasst das `onQuery` Ereignis, das alle Interaktionen im Fenster Messaging Erweiterung verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="df733-119">Most of your work involves the `onQuery` event, which handles all interactions in the messaging extension window.</span></span>

<span data-ttu-id="df733-120">Wenn Sie im `canUpdateConfiguration` Manifest `true` auf festlegen, aktivieren Sie das Menüelement **Einstellungen** für Ihre Messaging Erweiterung und müssen auch verarbeiten `onQuerySettingsUrl` und. `onSettingsUpdate`</span><span class="sxs-lookup"><span data-stu-id="df733-120">If you set `canUpdateConfiguration` to `true` in the manifest, you enable the **Settings** menu item for your messaging extension and must also handle `onQuerySettingsUrl` and `onSettingsUpdate`.</span></span>

### <a name="handle-onquery-events"></a><span data-ttu-id="df733-121">Behandeln von onquery-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="df733-121">Handle onQuery events</span></span>

<span data-ttu-id="df733-122">Eine Messaging Erweiterung empfängt ein `onQuery` Ereignis, wenn im Fenster Messaging Erweiterung etwas passiert oder an das Fenster gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="df733-122">A messaging extension receives an `onQuery` event when anything happens in the messaging extension window or is sent to the window.</span></span>

<span data-ttu-id="df733-123">Wenn Ihre Messaging-Erweiterung eine Konfigurationsseite verwendet, `onQuery` sollte Ihr Handler zunächst auf gespeicherte Konfigurationsinformationen überprüfen; Wenn die Messaging Erweiterung nicht konfiguriert ist, geben `config` Sie eine Antwort mit einem Link zu ihrer Konfigurationsseite zurück.</span><span class="sxs-lookup"><span data-stu-id="df733-123">If your messaging extension uses a configuration page, your handler for `onQuery` should first check for any stored configuration information; if the messaging extension isn't configured, return a `config` response with a link to your configuration page.</span></span> <span data-ttu-id="df733-124">Beachten Sie, dass die Antwort von der Konfigurationsseite auch von `onQuery`behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="df733-124">Be aware that the response from the configuration page is also handled by `onQuery`.</span></span> <span data-ttu-id="df733-125">(Die einzige Ausnahme ist, wenn die Konfigurationsseite vom Handler für `onQuerySettingsUrl`aufgerufen wird; siehe den folgenden Abschnitt.)</span><span class="sxs-lookup"><span data-stu-id="df733-125">(The sole exception is when the configuration page is called by the handler for `onQuerySettingsUrl`; see the following section.)</span></span>

<span data-ttu-id="df733-126">Wenn Ihre Messaging-Erweiterung Authentifizierung erfordert, überprüfen Sie die Benutzerstatusinformationen; Wenn der Benutzer nicht angemeldet ist, befolgen Sie die Anweisungen im Abschnitt [Authentifizierung](#authentication) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="df733-126">If your messaging extension requires authentication, check the user state information; if the user isn't signed in, follow the instructions in the [Authentication](#authentication) section later in this topic.</span></span>

<span data-ttu-id="df733-127">Überprüfen Sie als `initialRun` nächstes, ob festgelegt ist; Wenn dies der Fall ist, führen Sie die entsprechenden Schritte aus, beispielsweise Anweisungen oder eine Liste von Antworten.</span><span class="sxs-lookup"><span data-stu-id="df733-127">Next, check whether `initialRun` is set; if so, take appropriate action, such as providing instructions or a list of responses.</span></span>

<span data-ttu-id="df733-128">Der Rest Ihres Handlers `onQuery` fordert den Benutzer zur Eingabe von Informationen auf, zeigt eine Liste mit Vorschau Karten an und gibt die vom Benutzer ausgewählte Karte zurück.</span><span class="sxs-lookup"><span data-stu-id="df733-128">The remainder of your handler for `onQuery` prompts the user for information, displays a list of preview cards, and returns the card selected by the user.</span></span>

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a><span data-ttu-id="df733-129">Behandeln von onQuerySettingsUrl-und onSettingsUpdate-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="df733-129">Handle onQuerySettingsUrl and onSettingsUpdate events</span></span>

<span data-ttu-id="df733-130">Die `onQuerySettingsUrl` - `onSettingsUpdate` und-Ereignisse werden zusammenarbeiten, um das Menüelement **Einstellungen** zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="df733-130">The `onQuerySettingsUrl` and `onSettingsUpdate` events work together to enable the **Settings** menu item.</span></span>

![Screenshots des Menüelements "Speicherorte von Einstellungen"](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

<span data-ttu-id="df733-132">Der Handler für `onQuerySettingsUrl` gibt die URL für die Konfigurationsseite zurück; Nachdem die Konfigurationsseite geschlossen wurde, wird der `onSettingsUpdate` zurückgegebene Status vom Handler für akzeptiert und gespeichert.</span><span class="sxs-lookup"><span data-stu-id="df733-132">Your handler for `onQuerySettingsUrl` returns the URL for the configuration page; after the configuration page closes, your handler for `onSettingsUpdate` accepts and saves the returned state.</span></span> <span data-ttu-id="df733-133">(Dies ist der einzige Fall, `onQuery` bei dem die Antwort *nicht* von der Konfigurationsseite empfangen wird.)</span><span class="sxs-lookup"><span data-stu-id="df733-133">(This is the one case in which `onQuery` *doesn't* receive the response from the configuration page.)</span></span>

## <a name="receive-and-respond-to-queries"></a><span data-ttu-id="df733-134">Empfangen und beantworten von Abfragen</span><span class="sxs-lookup"><span data-stu-id="df733-134">Receive and respond to queries</span></span>

<span data-ttu-id="df733-135">Jede Anforderung an Ihre Messaging Erweiterung erfolgt über ein `Activity` Objekt, das an die Rückruf-URL gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="df733-135">Every request to your messaging extension is done via an `Activity` object that is posted to your callback URL.</span></span> <span data-ttu-id="df733-136">Die Anforderung enthält Informationen zum Benutzer Befehl wie ID und Parameterwerte.</span><span class="sxs-lookup"><span data-stu-id="df733-136">The request contains information about the user command, such as ID and parameter values.</span></span> <span data-ttu-id="df733-137">Die Anforderung liefert auch Metadaten zu dem Kontext, in dem Ihre Erweiterung aufgerufen wurde, einschließlich Benutzer-und Mandanten-ID sowie Chat-ID oder Kanal-und Team-IDs.</span><span class="sxs-lookup"><span data-stu-id="df733-137">The request also supplies metadata about the context in which your extension was invoked, including user and tenant ID, along with chat ID or channel and team IDs.</span></span>

### <a name="receive-user-requests"></a><span data-ttu-id="df733-138">Empfangen von Benutzeranforderungen</span><span class="sxs-lookup"><span data-stu-id="df733-138">Receive user requests</span></span>

<span data-ttu-id="df733-139">Wenn ein Benutzer eine Abfrage ausführt, sendet Microsoft Teams Ihrem Dienst ein Standardmäßiges `Activity` bot-Framework-Objekt.</span><span class="sxs-lookup"><span data-stu-id="df733-139">When a user performs a query, Microsoft Teams sends your service a standard Bot Framework `Activity` object.</span></span> <span data-ttu-id="df733-140">Ihr Dienst sollte seine Logik für einen `Activity` ausführen, der `type` auf `invoke` einen unter `name` stützten `composeExtension` Typ festgelegt und festgelegt hat, wie in der folgenden Tabelle dargestellt.</span><span class="sxs-lookup"><span data-stu-id="df733-140">Your service should perform its logic for an `Activity` that has `type` set to `invoke` and `name` set to a supported `composeExtension` type, as shown in the following table.</span></span>

<span data-ttu-id="df733-141">Zusätzlich zu den standardmäßigen bot-Aktivitätseigenschaften enthält die Nutzlast die folgenden Anforderungs Metadaten:</span><span class="sxs-lookup"><span data-stu-id="df733-141">In addition to the standard bot activity properties, the payload contains the following request metadata:</span></span>

|<span data-ttu-id="df733-142">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="df733-142">Property name</span></span>|<span data-ttu-id="df733-143">Zweck</span><span class="sxs-lookup"><span data-stu-id="df733-143">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="df733-144">Typ der Anforderung; muss sein `invoke`.</span><span class="sxs-lookup"><span data-stu-id="df733-144">Type of request; must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="df733-145">Der Typ des Befehls, der für den Dienst ausgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="df733-145">Type of command that is issued to your service.</span></span> <span data-ttu-id="df733-146">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="df733-146">Currently the following types are supported:</span></span> <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| <span data-ttu-id="df733-147">Die ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="df733-147">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="df733-148">Der Name des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="df733-148">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="df733-149">Azure Active Directory Objekt-ID des Benutzers, der die Anforderung gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="df733-149">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="df733-150">Azure Active Directory Mandanten-ID.</span><span class="sxs-lookup"><span data-stu-id="df733-150">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="df733-151">Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist).</span><span class="sxs-lookup"><span data-stu-id="df733-151">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="df733-152">Team-ID (wenn die Anforderung in einem Kanal erfolgt ist).</span><span class="sxs-lookup"><span data-stu-id="df733-152">Team ID (if the request was made in a channel).</span></span> |
|<span data-ttu-id="df733-153">`clientInfo`Entität</span><span class="sxs-lookup"><span data-stu-id="df733-153">`clientInfo` entity</span></span> | <span data-ttu-id="df733-154">Zusätzliche Metadaten zum Client, beispielsweise Gebietsschema/Sprache und Typ des Clients.</span><span class="sxs-lookup"><span data-stu-id="df733-154">Additional metadata about the client, such as locale/language and type of client.</span></span> |

<span data-ttu-id="df733-155">Die Anforderungsparameter selbst werden im Value-Objekt gefunden, das die folgenden Eigenschaften enthält:</span><span class="sxs-lookup"><span data-stu-id="df733-155">The request parameters itself are found in the value object, which includes the following properties:</span></span>

| <span data-ttu-id="df733-156">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="df733-156">Property name</span></span> | <span data-ttu-id="df733-157">Zweck</span><span class="sxs-lookup"><span data-stu-id="df733-157">Purpose</span></span> |
|---|---|
| `commandId` | <span data-ttu-id="df733-158">Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht.</span><span class="sxs-lookup"><span data-stu-id="df733-158">The name of the command invoked by the user, matching one of the commands declared in the app manifest.</span></span> |
| `parameters` | <span data-ttu-id="df733-159">Array von Parametern.</span><span class="sxs-lookup"><span data-stu-id="df733-159">Array of parameters.</span></span> <span data-ttu-id="df733-160">Jedes Parameter-Objekt enthält den Namen des Parameters sowie den vom Benutzer bereitgestellten Parameterwert.</span><span class="sxs-lookup"><span data-stu-id="df733-160">Each parameter object contains the parameter name, along with the parameter value provided by the user.</span></span> |
| `queryOptions` | <span data-ttu-id="df733-161">Paginierung Parameter:</span><span class="sxs-lookup"><span data-stu-id="df733-161">Pagination parameters:</span></span> <br><span data-ttu-id="df733-162">`skip`: Skip count für diese Abfrage</span><span class="sxs-lookup"><span data-stu-id="df733-162">`skip`: skip count for this query</span></span> <br><span data-ttu-id="df733-163">`count`: Anzahl der zurückzugebenden Elemente</span><span class="sxs-lookup"><span data-stu-id="df733-163">`count`: number of elements to return</span></span> |

#### <a name="request-example"></a><span data-ttu-id="df733-164">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="df733-164">Request example</span></span>

```json
{
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "searchKeywords",
        "value": "Toronto"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  "type": "invoke",
  "timestamp": "2017-05-01T15:45:51.876Z",
  "localTimestamp": "2017-05-01T08:45:51.876-07:00",
  "id": "f:622749630322482883",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
    "name": "Larry Jin",
    "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
  },
  "conversation": {
    "id": "19:skypespaces_8198cfe0dd2647ae91930f0974768a40@thread.skype"
  },
  "recipient": {
    "id": "28:b4922ea1-5315-4fd0-9b21-d941ab06e39f",
    "name": "TheComposeExtensionDev"
  },
  "entities": [
    {
      "locale": "en-US",
      "country": "US",
      "platform": "Windows",
      "timezone": "America/Los_Angeles",
      "type": "clientInfo"
    }
  ]
}
```

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a><span data-ttu-id="df733-165">Empfangen von Anforderungen von Links, die in das Meldungsfeld "Verfassen" eingefügt werden</span><span class="sxs-lookup"><span data-stu-id="df733-165">Receive requests from links inserted into the compose message box</span></span>

<span data-ttu-id="df733-166">Alternativ (oder zusätzlich) zum Durchsuchen Ihres externen Diensts können Sie eine URL verwenden, die in das Meldungsfeld verfassen eingefügt wurde, um Ihren Dienst abzufragen und eine Karte zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="df733-166">As an alternative (or in addition) to searching your external service, you can use a URL inserted into the compose message box to query your service and return a card.</span></span> <span data-ttu-id="df733-167">Im Screenshot unten hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die von der Messaging Erweiterung in eine Karte aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="df733-167">In the screenshot below a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Beispiel für eine Link-Entfaltung](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

<span data-ttu-id="df733-169">Damit Ihre Messaging Erweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array wie im folgenden Beispiel zu Ihrem App-Manifest hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="df733-169">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below:</span></span>

```json
"composeExtensions": [
  {
    "botId": "abc123456-ab12-ab12-ab12-abcdef123456",
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.trackeddomain.com"
          ]
        }
      }
    ]
  }
]
```

<span data-ttu-id="df733-170">Nachdem Sie die Domäne zum Überwachen des App-Manifests hinzugefügt haben, müssen Sie Ihren botcode so ändern, dass er auf die unten gezeigte Invoke-Anforderung [antwortet](#respond-to-user-requests) .</span><span class="sxs-lookup"><span data-stu-id="df733-170">Once you've added the domain to listen on to the app manifest, you'll need to change your bot code to [respond](#respond-to-user-requests) to the below invoke request.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="df733-171">Wenn Ihre APP mehrere Elemente zurückgibt, wird nur die erste verwendet.</span><span class="sxs-lookup"><span data-stu-id="df733-171">If your app returns multiple items only the first will be used.</span></span>

### <a name="respond-to-user-requests"></a><span data-ttu-id="df733-172">Reagieren auf Benutzeranforderungen</span><span class="sxs-lookup"><span data-stu-id="df733-172">Respond to user requests</span></span>

<span data-ttu-id="df733-173">Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone http-Anforderung an Ihren Dienst aus.</span><span class="sxs-lookup"><span data-stu-id="df733-173">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service.</span></span> <span data-ttu-id="df733-174">An diesem Zeitpunkt hat der Code 5 Sekunden, um eine HTTP-Antwort auf die Anforderung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="df733-174">At that point, your code has 5 seconds to provide an HTTP response to the request.</span></span> <span data-ttu-id="df733-175">Während dieser Zeit kann der Dienst zusätzliche Suchvorgänge durchführen oder eine andere Geschäftslogik, die für die Zustellung der Anforderung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="df733-175">During this time, your service can perform additional lookup, or any other business logic needed to serve the request.</span></span>

<span data-ttu-id="df733-176">Ihr Dienst sollte mit den Ergebnissen Antworten, die mit der Benutzerabfrage übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="df733-176">Your service should respond with the results matching the user query.</span></span> <span data-ttu-id="df733-177">Die Antwort muss einen HTTP-Statuscode `200 OK` und ein gültiges Application/JSON-Objekt mit folgendem Text angeben:</span><span class="sxs-lookup"><span data-stu-id="df733-177">The response must indicate an HTTP status code of `200 OK` and a valid application/json object with the following body:</span></span>

|<span data-ttu-id="df733-178">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="df733-178">Property name</span></span>|<span data-ttu-id="df733-179">Zweck</span><span class="sxs-lookup"><span data-stu-id="df733-179">Purpose</span></span>|
|---|---|
|`composeExtension`|<span data-ttu-id="df733-180">Antwortumschlag auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="df733-180">Top-level response envelope.</span></span>|
|`composeExtension.type`|<span data-ttu-id="df733-181">Typ der Antwort.</span><span class="sxs-lookup"><span data-stu-id="df733-181">Type of response.</span></span> <span data-ttu-id="df733-182">Die folgenden Typen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="df733-182">The following types are supported:</span></span> <br><span data-ttu-id="df733-183">`result`: zeigt eine Liste der Suchergebnisse an.</span><span class="sxs-lookup"><span data-stu-id="df733-183">`result`: displays a list of search results</span></span> <br><span data-ttu-id="df733-184">`auth`: der Benutzer wird aufgefordert, sich zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="df733-184">`auth`: asks the user to authenticate</span></span> <br><span data-ttu-id="df733-185">`config`: der Benutzer wird aufgefordert, die Messaging Erweiterung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="df733-185">`config`: asks the user to set up the messaging extension</span></span> <br><span data-ttu-id="df733-186">`message`: zeigt eine nur-Text-Nachricht an.</span><span class="sxs-lookup"><span data-stu-id="df733-186">`message`: displays a plain text message</span></span> |
|`composeExtension.attachmentLayout`|<span data-ttu-id="df733-187">Gibt das Layout der Anlagen an.</span><span class="sxs-lookup"><span data-stu-id="df733-187">Specifies the layout of the attachments.</span></span> <span data-ttu-id="df733-188">Wird für Antworten vom Typ `result`verwendet.</span><span class="sxs-lookup"><span data-stu-id="df733-188">Used for responses of type `result`.</span></span> <br><span data-ttu-id="df733-189">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="df733-189">Currently the following types are supported:</span></span> <br><span data-ttu-id="df733-190">`list`: eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten</span><span class="sxs-lookup"><span data-stu-id="df733-190">`list`: a list of card objects containing thumbnail, title, and text fields</span></span> <br><span data-ttu-id="df733-191">`grid`: ein Raster von Miniaturbildern</span><span class="sxs-lookup"><span data-stu-id="df733-191">`grid`: a grid of thumbnail images</span></span> |
|`composeExtension.attachments`|<span data-ttu-id="df733-192">Array gültiger Attachment-Objekte.</span><span class="sxs-lookup"><span data-stu-id="df733-192">Array of valid attachment objects.</span></span> <span data-ttu-id="df733-193">Wird für Antworten vom Typ `result`verwendet.</span><span class="sxs-lookup"><span data-stu-id="df733-193">Used for responses of type `result`.</span></span> <br><span data-ttu-id="df733-194">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="df733-194">Currently the following types are supported:</span></span> <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|<span data-ttu-id="df733-195">Vorgeschlagene Aktionen.</span><span class="sxs-lookup"><span data-stu-id="df733-195">Suggested actions.</span></span> <span data-ttu-id="df733-196">Wird für Antworten vom Typ `auth` oder `config`verwendet.</span><span class="sxs-lookup"><span data-stu-id="df733-196">Used for responses of type `auth` or `config`.</span></span> |
|`composeExtension.text`|<span data-ttu-id="df733-197">Anzuzeigende Meldung.</span><span class="sxs-lookup"><span data-stu-id="df733-197">Message to display.</span></span> <span data-ttu-id="df733-198">Wird für Antworten vom Typ `message`verwendet.</span><span class="sxs-lookup"><span data-stu-id="df733-198">Used for responses of type `message`.</span></span> |

#### <a name="response-card-types-and-previews"></a><span data-ttu-id="df733-199">Antwortkarten Typen und-Vorschauen</span><span class="sxs-lookup"><span data-stu-id="df733-199">Response card types and previews</span></span>

<span data-ttu-id="df733-200">Wir unterstützen die folgenden Anlagentypen:</span><span class="sxs-lookup"><span data-stu-id="df733-200">We support the following attachment types:</span></span>

* [<span data-ttu-id="df733-201">Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="df733-201">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="df733-202">Hero Card</span><span class="sxs-lookup"><span data-stu-id="df733-202">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="df733-203">Office 365-Anschluss Karte</span><span class="sxs-lookup"><span data-stu-id="df733-203">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="df733-204">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="df733-204">Adaptive card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="df733-205">Eine Übersicht finden Sie unter [Cards](~/task-modules-and-cards/what-are-cards.md) .</span><span class="sxs-lookup"><span data-stu-id="df733-205">See [Cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

<span data-ttu-id="df733-206">Weitere Informationen zur Verwendung der Miniaturansicht-und Hero-Kartentypen finden Sie unter [Add Cards and Card Actions](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="df733-206">To learn how to use the thumbnail and hero card types, see [Add cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="df733-207">Weitere Informationen zur Office 365-Verbindungskarte finden Sie unter [using Office 365 Connector Cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="df733-207">For additional documentation regarding the Office 365 Connector card, see [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="df733-208">Die Ergebnisliste wird auf der Microsoft Teams-Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="df733-208">The result list is displayed in the Microsoft Teams UI with a preview of each item.</span></span> <span data-ttu-id="df733-209">Die Vorschau wird auf eine von zwei Arten generiert:</span><span class="sxs-lookup"><span data-stu-id="df733-209">The preview is generated in one of two ways:</span></span>

* <span data-ttu-id="df733-210">Verwenden der `preview` -Eigenschaft innerhalb `attachment` des-Objekts.</span><span class="sxs-lookup"><span data-stu-id="df733-210">Using the `preview` property within the `attachment` object.</span></span> <span data-ttu-id="df733-211">Die `preview` Anlage kann nur eine Hero-oder Thumbnail-Karte sein.</span><span class="sxs-lookup"><span data-stu-id="df733-211">The `preview` attachment can only be a Hero or Thumbnail card.</span></span>
* <span data-ttu-id="df733-212">Extrahiert aus den Eigenschaften `title`Basic `text`, und `image` und der Anlage.</span><span class="sxs-lookup"><span data-stu-id="df733-212">Extracted from the basic `title`, `text`, and `image` properties of the attachment.</span></span> <span data-ttu-id="df733-213">Diese werden nur verwendet, wenn `preview` die Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="df733-213">These are used only if the `preview` property is not set and these properties are available.</span></span>

<span data-ttu-id="df733-214">Sie können eine Vorschau einer adaptiven oder Office 365-connectorkarte in der Ergebnisliste anzeigen, indem Sie einfach die zugehörige Preview-Eigenschaft festlegen; Dies ist nicht erforderlich, wenn die Ergebnisse bereits Hero-oder Thumbnail-Karten sind.</span><span class="sxs-lookup"><span data-stu-id="df733-214">You can display a preview of an Adaptive or Office 365 Connector card in the result list simply by setting its preview property; this is not necessary if the results are already hero or thumbnail cards.</span></span> <span data-ttu-id="df733-215">Wenn Sie die Vorschau Anlage verwenden, muss es sich entweder um eine Hero-oder eine Miniatur Ansichtskarte handeln.</span><span class="sxs-lookup"><span data-stu-id="df733-215">If you use the preview attachment, it must be either a Hero or Thumbnail card.</span></span> <span data-ttu-id="df733-216">Wenn keine Preview-Eigenschaft angegeben wird, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="df733-216">If no preview property is specified, the preview of the card will fail and nothing will be displayed.</span></span>

#### <a name="response-example"></a><span data-ttu-id="df733-217">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="df733-217">Response example</span></span>

<span data-ttu-id="df733-218">In diesem Beispiel wird eine Antwort mit zwei Ergebnissen gezeigt, wobei unterschiedliche Kartenformate gemischt werden: Office 365-Konnektor und adaptiv.</span><span class="sxs-lookup"><span data-stu-id="df733-218">This example shows a response with two results, mixing different card formats: Office 365 Connector and Adaptive.</span></span> <span data-ttu-id="df733-219">Während Sie wahrscheinlich mit einem Kartenformat in ihrer Antwort bleiben möchten, wird gezeigt, wie die `preview` Eigenschaft der einzelnen Elemente in der `attachments` Auflistung explizit eine Vorschau im Hero-oder Miniatur Ansichtsformat definieren muss, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="df733-219">While you'll likely want to stick with one card format in your response, it shows how the `preview` property of each element in the `attachments` collection must explicitly define a preview in hero or thumbnail format as described above.</span></span>

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "attachments": [
      {
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        }
      },
      {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Container",
              "items": [
                {
                  "type": "TextBlock",
                  "text": "Microsoft Corp (NASDAQ: MSFT)",
                  "size": "medium",
                  "isSubtle": true
                },
                {
                  "type": "TextBlock",
                  "text": "September 19, 4:00 PM EST",
                  "isSubtle": true
                }
              ]
            },
            {
              "type": "Container",
              "spacing": "none",
              "items": [
                {
                  "type": "ColumnSet",
                  "columns": [
                    {
                      "type": "Column",
                      "width": "stretch",
                      "items": [
                        {
                          "type": "TextBlock",
                          "text": "75.30",
                          "size": "extraLarge"
                        },
                        {
                          "type": "TextBlock",
                          "text": "▼ 0.20 (0.32%)",
                          "size": "small",
                          "color": "attention",
                          "spacing": "none"
                        }
                      ]
                    },
                    {
                      "type": "Column",
                      "width": "auto",
                      "items": [
                        {
                          "type": "FactSet",
                          "facts": [
                            {
                              "title": "Open",
                              "value": "62.24"
                            },
                            {
                              "title": "High",
                              "value": "62.98"
                            },
                            {
                              "title": "Low",
                              "value": "62.20"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ],
          "version": "1.0"
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "Microsoft Corp (NASDAQ: MSFT)",
            "text": "75.30 ▼ 0.20 (0.32%)"
          }
        }
      }
    ]
  }
}
```

### <a name="default-query"></a><span data-ttu-id="df733-220">Standardabfrage</span><span class="sxs-lookup"><span data-stu-id="df733-220">Default query</span></span>

<span data-ttu-id="df733-221">Wenn Sie im `initialRun` Manifest `true` auf festlegen, gibt Microsoft Teams eine "Standard"-Abfrage aus, wenn der Benutzer die Messaging Erweiterung zum ersten Mal öffnet.</span><span class="sxs-lookup"><span data-stu-id="df733-221">If you set `initialRun` to `true` in the manifest, Microsoft Teams issues a "default" query when the user first opens the messaging extension.</span></span> <span data-ttu-id="df733-222">Ihr Dienst kann auf diese Abfrage mit einer Reihe von vorab aufgefüllten Ergebnissen Antworten.</span><span class="sxs-lookup"><span data-stu-id="df733-222">Your service can respond to this query with a set of prepopulated results.</span></span> <span data-ttu-id="df733-223">Dies kann hilfreich sein, um beispielsweise kürzlich angezeigte Elemente, Favoriten oder andere Informationen anzuzeigen, die nicht von der Benutzereingabe abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="df733-223">This can be useful for displaying, for instance, recently viewed items, favorites, or any other information that is not dependent on user input.</span></span>

<span data-ttu-id="df733-224">Die Standardabfrage hat dieselbe Struktur wie jede reguläre Benutzerabfrage, mit Ausnahme eines Parameters `initialRun` , dessen Zeichen `true`folgen Wert ist.</span><span class="sxs-lookup"><span data-stu-id="df733-224">The default query has the same structure as any regular user query, except with a parameter `initialRun` whose string value is `true`.</span></span>

#### <a name="request-example-for-a-default-query"></a><span data-ttu-id="df733-225">Anforderungs Beispiel für eine Standardabfrage</span><span class="sxs-lookup"><span data-stu-id="df733-225">Request example for a default query</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "initialRun",
        "value": "true"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  ⋮
}
```

## <a name="identify-the-user"></a><span data-ttu-id="df733-226">Identifizieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="df733-226">Identify the user</span></span>

<span data-ttu-id="df733-227">Jede Anforderung an ihre Dienste umfasst die verborgene ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory Objekt-ID.</span><span class="sxs-lookup"><span data-stu-id="df733-227">Every request to your services includes the obfuscated ID of the user that performed the request, as well as the user's display name and Azure Active Directory object ID.</span></span>

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

<span data-ttu-id="df733-228">Die `id` Werte `aadObjectId` und sind garantiert die des authentifizierten Teams-Benutzers.</span><span class="sxs-lookup"><span data-stu-id="df733-228">The `id` and `aadObjectId` values are guaranteed to be that of the authenticated Teams user.</span></span> <span data-ttu-id="df733-229">Sie können als Schlüssel zum Nachschlagen von Anmeldeinformationen oder einem beliebigen zwischengespeicherten Zustand in Ihrem Dienst verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="df733-229">They can be used as keys to look up credentials or any cached state in your service.</span></span> <span data-ttu-id="df733-230">Darüber hinaus enthält jede Anforderung die Azure Active Directory Mandanten-ID des Benutzers, die zum Identifizieren der Organisation des Benutzers verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="df733-230">In addition, each request contains the Azure Active Directory tenant ID of the user, which can be used to identify the user’s organization.</span></span> <span data-ttu-id="df733-231">Wenn zutreffend, enthält die Anforderung auch die Team-und Kanal-IDs, aus denen die Anforderung stammt.</span><span class="sxs-lookup"><span data-stu-id="df733-231">If applicable, the request also contains the team and channel IDs from which the request originated.</span></span>

## <a name="authentication"></a><span data-ttu-id="df733-232">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="df733-232">Authentication</span></span>

<span data-ttu-id="df733-233">Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messaging Erweiterung verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="df733-233">If your service requires user authentication, you need to sign in the user before he or she can use the messaging extension.</span></span> <span data-ttu-id="df733-234">Wenn Sie einen bot oder eine Registerkarte geschrieben haben, die den Benutzer signiert, sollte dieser Abschnitt vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="df733-234">If you have written a bot or a tab that signs in the user, this section should be familiar.</span></span>

<span data-ttu-id="df733-235">Die Sequenz lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="df733-235">The sequence is as follows:</span></span>

1. <span data-ttu-id="df733-236">Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an den Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="df733-236">User issues a query, or the default query is automatically sent to your service.</span></span>
2. <span data-ttu-id="df733-237">Der Dienst überprüft, ob der Benutzer zuerst authentifiziert wurde, indem er die Benutzer-ID des Teams überprüft.</span><span class="sxs-lookup"><span data-stu-id="df733-237">Your service checks whether the user has first authenticated by inspecting the Teams user ID.</span></span>
3. <span data-ttu-id="df733-238">Wenn der Benutzer nicht authentifiziert wurde, senden Sie eine `auth` Antwort mit einer `openUrl` vorgeschlagenen Aktion einschließlich der Authentifizierungs-URL zurück.</span><span class="sxs-lookup"><span data-stu-id="df733-238">If the user has not authenticated, send back an `auth` response with an `openUrl` suggested action including the authentication URL.</span></span>
4. <span data-ttu-id="df733-239">Der Microsoft Teams-Client startet ein Popupfenster, das Ihre Webseite unter Verwendung der angegebenen Authentifizierungs-URL hostet.</span><span class="sxs-lookup"><span data-stu-id="df733-239">The Microsoft Teams client launches a pop-up window hosting your webpage using the given authentication URL.</span></span>
5. <span data-ttu-id="df733-240">Nachdem sich der Benutzer angemeldet hat, sollten Sie das Fenster schließen und einen "Authentifizierungscode" an den Microsoft Teams-Client senden.</span><span class="sxs-lookup"><span data-stu-id="df733-240">After the user signs in, you should close your window and send an "authentication code" to the Teams client.</span></span>
6. <span data-ttu-id="df733-241">Der Microsoft Teams-Client gibt dann die Abfrage erneut an Ihren Dienst aus, der den in Schritt 5 übergebenen Authentifizierungscode enthält.</span><span class="sxs-lookup"><span data-stu-id="df733-241">The Teams client then reissues the query to your service, which includes the authentication code passed in step 5.</span></span>

<span data-ttu-id="df733-242">Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem in Schritt 5 übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="df733-242">Your service should verify that the authentication code received in step 6 matches the one from step 5.</span></span> <span data-ttu-id="df733-243">Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmelde Ablauf vorzutäuschen oder zu gefährden.</span><span class="sxs-lookup"><span data-stu-id="df733-243">This ensures that a malicious user does not try to spoof or compromise the sign-in flow.</span></span> <span data-ttu-id="df733-244">Dies effektiv "schließt die Schleife", um die sichere Authentifizierungssequenz abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="df733-244">This effectively "closes the loop" to finish the secure authentication sequence.</span></span>

### <a name="respond-with-a-sign-in-action"></a><span data-ttu-id="df733-245">Reagieren mit einer Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="df733-245">Respond with a sign-in action</span></span>

<span data-ttu-id="df733-246">Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, Antworten Sie mit einer vorgeschlagenen Aktion `openUrl` vom Typ, die die Authentifizierungs-URL enthält.</span><span class="sxs-lookup"><span data-stu-id="df733-246">To prompt an unauthenticated user to sign in, respond with a suggested action of type `openUrl` that includes the authentication URL.</span></span>

#### <a name="response-example-for-a-sign-in-action"></a><span data-ttu-id="df733-247">Antwortbeispiel für eine Anmeldeaktion</span><span class="sxs-lookup"><span data-stu-id="df733-247">Response example for a sign-in action</span></span>

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
> <span data-ttu-id="df733-248">Damit die Anmelde Umgebung in einem Teams-Popup gehostet werden kann, muss der Domänenteil der URL in der Liste der gültigen Domänen in Ihrer APP aufgeführt sein.</span><span class="sxs-lookup"><span data-stu-id="df733-248">For the sign-in experience to be hosted in a Teams pop-up, the domain portion of the URL must be in your app’s list of valid domains.</span></span> <span data-ttu-id="df733-249">(Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifest-Schema.)</span><span class="sxs-lookup"><span data-stu-id="df733-249">(See [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema.)</span></span>

### <a name="start-the-sign-in-flow"></a><span data-ttu-id="df733-250">Starten des Anmelde Flusses</span><span class="sxs-lookup"><span data-stu-id="df733-250">Start the sign-in flow</span></span>

<span data-ttu-id="df733-251">Ihre Anmelde Erfahrung sollte reagieren und in ein Popupfenster passt.</span><span class="sxs-lookup"><span data-stu-id="df733-251">Your sign-in experience should be responsive and fit within a popup window.</span></span> <span data-ttu-id="df733-252">Sie sollte in das [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübergabe verwendet.</span><span class="sxs-lookup"><span data-stu-id="df733-252">It should integrate with the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client), which uses message passing.</span></span>

<span data-ttu-id="df733-253">Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams durchführen, muss der Code im Fenster zuerst `microsoftTeams.initialize()`aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="df733-253">As with other embedded experiences running inside Microsoft Teams, your code inside the window needs to first call `microsoftTeams.initialize()`.</span></span> <span data-ttu-id="df733-254">Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Benutzer-ID des Teams an das Fenster übergeben, das dann an die OAuth-Anmelde-URL übergeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="df733-254">If your code performs an OAuth flow, you can pass the Teams user ID into your window, which then can pass it to the OAuth sign-in URL.</span></span>

### <a name="complete-the-sign-in-flow"></a><span data-ttu-id="df733-255">Abschließen des Anmelde Flusses</span><span class="sxs-lookup"><span data-stu-id="df733-255">Complete the sign-in flow</span></span>

<span data-ttu-id="df733-256">Wenn die Anmeldeanforderung abgeschlossen wird und zu Ihrer Seite zurückgeleitet wird, sollten Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="df733-256">When the sign-in request completes and redirects back to your page, it should perform the following steps:</span></span>

1. <span data-ttu-id="df733-257">Generieren Sie einen Sicherheitscode.</span><span class="sxs-lookup"><span data-stu-id="df733-257">Generate a security code.</span></span> <span data-ttu-id="df733-258">(Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst Zwischenspeichern, zusammen mit den Anmeldeinformationen, die über den Anmelde Fluss abgerufen werden (beispielsweise OAuth 2,0-Token).</span><span class="sxs-lookup"><span data-stu-id="df733-258">(This can be a random number.) You need to cache this code on your service, along with the credentials obtained through the sign-in flow (such as OAuth 2.0 tokens).</span></span>
2. <span data-ttu-id="df733-259">Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode an, und übergeben Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="df733-259">Call `microsoftTeams.authentication.notifySuccess` and pass the security code.</span></span>

<span data-ttu-id="df733-260">Zu diesem Zeitpunkt wird das Fenster geschlossen, und die Steuerung wird an den Microsoft Teams-Client übergeben.</span><span class="sxs-lookup"><span data-stu-id="df733-260">At this point, the window closes and control is passed to the Teams client.</span></span> <span data-ttu-id="df733-261">Der Client kann jetzt die ursprüngliche Benutzerabfrage erneut ausgeben, zusammen mit dem Sicherheitscode in der `state` -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="df733-261">The client now can reissue the original user query, along with the security code in the `state` property.</span></span> <span data-ttu-id="df733-262">Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="df733-262">Your code can use the security code to look up the credentials stored earlier to complete the authentication sequence and then complete the user request.</span></span>

#### <a name="reissued-request-example"></a><span data-ttu-id="df733-263">Beispiel für eine erneut aufgegebene Anforderung</span><span class="sxs-lookup"><span data-stu-id="df733-263">Reissued request example</span></span>

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

## <a name="sdk-support"></a><span data-ttu-id="df733-264">SDK-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="df733-264">SDK support</span></span>

### <a name="net"></a><span data-ttu-id="df733-265">.NET</span><span class="sxs-lookup"><span data-stu-id="df733-265">.NET</span></span>

<span data-ttu-id="df733-266">Wenn Sie Abfragen mit dem bot Builder SDK für .net empfangen und verarbeiten möchten, können Sie den `invoke` Aktionstyp für die eingehende Aktivität überprüfen und dann die Hilfsmethode im NuGet-Paket " [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) " verwenden, um zu ermitteln, ob es sich um eine Messaging Erweiterungs Aktivität handelt.</span><span class="sxs-lookup"><span data-stu-id="df733-266">To receive and handle queries with the Bot Builder SDK for .NET, you can check for the `invoke` action type on the incoming activity and then use the helper method in the NuGet package [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) to determine whether it’s a messaging extension activity.</span></span>

#### <a name="example-code-in-net"></a><span data-ttu-id="df733-267">Beispielcode in .net</span><span class="sxs-lookup"><span data-stu-id="df733-267">Example code in .NET</span></span>

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
    if (activity.Type == ActivityTypes.Invoke) // Received an invoke
    {
        if (activity.IsComposeExtensionQuery())
        {
            // This is the response object that will get sent back to the messaging extension request.
            ComposeExtensionResponse invokeResponse = null;

            // This helper method gets the query as an object.
            var query = activity.GetComposeExtensionQueryData();

            if (query.CommandId != null && query.Parameters != null && query.Parameters.Count > 0)
            {
                // query.Parameters has the parameters sent by client
                var results = new ComposeExtensionResult()
                {
                    AttachmentLayout = "list",
                    Type = "result",
                    Attachments = new List<ComposeExtensionAttachment>(),
                };
                invokeResponse.ComposeExtension = results;
            }

            // Return the response
            return Request.CreateResponse<ComposeExtensionResponse>(HttpStatusCode.OK, invokeResponse);
        } else
        {
            // Handle other types of Invoke activities here.
        }
    } else {
      // Failure case catch-all.
      var response = Request.CreateResponse(HttpStatusCode.BadRequest);
      response.Content = new StringContent("Invalid request! This API supports only messaging extension requests. Check your query and try again");
      return response;
    }
}
```

### <a name="nodejs"></a><span data-ttu-id="df733-268">Node.js</span><span class="sxs-lookup"><span data-stu-id="df733-268">Node.js</span></span>

<span data-ttu-id="df733-269">Die Microsoft [Teams-Erweiterungen](https://www.npmjs.com/package/botbuilder-teams) für das bot Builder SDK für Node. js bieten Hilfsobjekte und-Methoden zum Vereinfachen des Empfangs, der Verarbeitung und der Reaktion auf Messaging Erweiterungsanforderungen.</span><span class="sxs-lookup"><span data-stu-id="df733-269">The [Teams extensions](https://www.npmjs.com/package/botbuilder-teams) for the Bot Builder SDK for Node.js provide helper objects and methods to simplify receiving, processing, and responding to messaging extension requests.</span></span>

#### <a name="example-code-in-nodejs"></a><span data-ttu-id="df733-270">Beispielcode in Node. js</span><span class="sxs-lookup"><span data-stu-id="df733-270">Example code in Node.js</span></span>

```javascript
require('dotenv').config();

import * as restify from 'restify';
import * as builder from 'botbuilder';
import * as teamBuilder from 'botbuilder-teams';

class App {
    run() {
        const server = restify.createServer();
        let teamChatConnector = new teamBuilder.TeamsChatConnector({
            appId: process.env.MICROSOFT_APP_ID,
            appPassword: process.env.MICROSOFT_APP_PASSWORD
        });

        // Command ID must match what's defined in manifest
        teamChatConnector.onQuery('<%= commandId %>',
            (event: builder.IEvent,
            query: teamBuilder.ComposeExtensionQuery,
            callback: (err: Error, result: teamBuilder.IComposeExtensionResponse, statusCode: number) => void) => {
                // Check for initialRun; i.e., when you should return default results
                // if (query.parameters[0].name === 'initialRun') {}

                // Check query.queryOptions.count and query.queryOptions.skip for paging

                // Return auth response
                // let response = teamBuilder.ComposeExtensionResponse.auth().actions([
                //     builder.CardAction.openUrl(null, 'https://authUrl', 'Please sign in')
                // ]).toResponse();

                // Return config response
                // let response = teamBuilder.ComposeExtensionResponse.config().actions([
                //     builder.CardAction.openUrl(null, 'https://configUrl', 'Please sign in')
                // ]).toResponse();

                // Return result response
                let response = teamBuilder.ComposeExtensionResponse.result('list').attachments([
                    new builder.ThumbnailCard()
                        .title('Test thumbnail card')
                        .text('This is a test thumbnail card')
                        .images([new builder.CardImage().url('https://bot-framework.azureedge.net/bot-icons-v1/bot-framework-default-9.png')])
                        .toAttachment()
                ]).toResponse();
                callback(null, response, 200);
            });
        server.post('/api/composeExtension', teamChatConnector.listen());
        server.listen(process.env.PORT, () => console.log(`listening to port:` + process.env.PORT));
    }
}

const app = new App();
app.run();
```