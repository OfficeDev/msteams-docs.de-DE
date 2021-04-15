---
title: Suchen mit Messagingerweiterungen
description: Beschreibt die Entwicklung suchbasierter Messagingerweiterungen
keywords: Suche nach Messagingerweiterungen für Teams-Messagingerweiterungen
ms.topic: how-to
ms.date: 07/20/2019
ms.openlocfilehash: 7a4074fe4f3a15621729f4c549d31dc90d98e714
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696105"
---
# <a name="search-with-messaging-extensions"></a>Suchen mit Messagingerweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Suchbasierte Messagingerweiterungen ermöglichen es Ihnen, Ihren Dienst zu abfragen und diese Informationen in Form einer Karte direkt in Ihre Nachricht zu posten.

![Beispiel für Eine Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird dies beschrieben.

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a>Nachrichtenerweiterungen des Suchtyps

Legen Sie für die suchbasierte Messagingerweiterung den `type` Parameter auf . `query` Im Folgenden finden Sie ein Beispiel für ein Manifest mit einem einzelnen Suchbefehl. Einer einzelnen Messagingerweiterung können bis zu 10 verschiedene Befehle zugeordnet sein. Dies kann sowohl mehrere Suchbefehle als auch mehrere aktionsbasierte Befehle umfassen.

#### <a name="complete-app-manifest-example"></a>Vollständiges Beispiel für das App-Manifest

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
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

### <a name="test-via-uploading"></a>Testen über Hochladen

Sie können Ihre Messagingerweiterung testen, indem Sie Ihre App hochladen.

Um Ihre Messagingerweiterung zu öffnen, navigieren Sie zu ihren Chats oder Kanälen. Wählen Sie **die** Schaltfläche Weitere Optionen (**&#8943;**) im Verfassenfeld aus, und wählen Sie Ihre Messagingerweiterung aus.

## <a name="add-event-handlers"></a>Hinzufügen von Ereignishandlern

Der Großteil Ihrer Arbeit umfasst das `onQuery` Ereignis, das alle Interaktionen im Messagingerweiterungsfenster behandelt.

Wenn Sie im Manifest auf festgelegt sind, aktivieren Sie das Menüelement Einstellungen für Ihre Messagingerweiterung und müssen auch `canUpdateConfiguration` `true` mit und  `onQuerySettingsUrl` `onSettingsUpdate` umgehen.

### <a name="handle-onquery-events"></a>Behandeln von onQuery-Ereignissen

Eine Messagingerweiterung empfängt ein Ereignis, wenn im Nachrichtenerweiterungsfenster etwas passiert `onQuery` oder an das Fenster gesendet wird.

Wenn Ihre #A0 eine Konfigurationsseite verwendet, sollte der Handler für zuerst nach gespeicherten Konfigurationsinformationen suchen. Wenn die Messagingerweiterung nicht konfiguriert ist, geben Sie eine Antwort mit einem Link zu Ihrer Konfigurationsseite `onQuery` `config` zurück. Beachten Sie, dass die Antwort von der Konfigurationsseite auch von verarbeitet `onQuery` wird. (Die einzige Ausnahme ist, wenn die Konfigurationsseite vom Handler für aufgerufen `onQuerySettingsUrl` wird. siehe folgenden Abschnitt.)

Wenn ihre Messagingerweiterung eine Authentifizierung erfordert, überprüfen Sie die Benutzerstatusinformationen. Wenn der Benutzer nicht angemeldet ist, befolgen Sie die Anweisungen im Abschnitt [Authentifizierung](#authentication) weiter unten in diesem Thema.

Überprüfen Sie als Nächstes, ob festgelegt ist. Falls ja, ergreifen Sie entsprechende Maßnahmen, z. B. Anweisungen oder `initialRun` eine Liste der Antworten.

Der Rest ihres Handlers fordert den Benutzer auf, Informationen zu erhalten, zeigt eine Liste der Vorschaukarten an und gibt die vom Benutzer ausgewählte `onQuery` Karte zurück.

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Behandeln von OnQuerySettingsUrl- und onSettingsUpdate-Ereignissen

The `onQuerySettingsUrl` and events work together to enable the `onSettingsUpdate` **Settings** menu item.

![Screenshots der Speicherorte des Menüelements Einstellungen](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

Der Handler für gibt die URL für die Konfigurationsseite zurück. Nachdem die Konfigurationsseite geschlossen wurde, akzeptiert und speichert der Handler für den `onQuerySettingsUrl` `onSettingsUpdate` zurückgegebenen Status. (Dies ist der fall, in dem `onQuery` *erhält die Antwort* nicht von der Konfigurationsseite.)

## <a name="receive-and-respond-to-queries"></a>Empfangen und Beantworten von Abfragen

Jede Anforderung an Ihre Messagingerweiterung erfolgt über ein `Activity` Objekt, das in Ihrer Rückruf-URL bereitgestellt wird. Die Anforderung enthält Informationen zum Benutzerbefehl, z. B. ID- und Parameterwerte. Die Anforderung stellt außerdem Metadaten zum Kontext bereit, in dem Ihre Erweiterung aufgerufen wurde, einschließlich Benutzer- und Mandanten-ID sowie Chat-ID oder Kanal- und Team-IDs.

### <a name="receive-user-requests"></a>Empfangen von Benutzeranforderungen

Wenn ein Benutzer eine Abfrage ausführt, sendet Microsoft Teams Ihrem Dienst ein Standardmäßiges Bot `Activity` Framework-Objekt. Ihr Dienst sollte seine Logik für einen Dienst ausführen, der auf einen unterstützten Typ festgelegt und auf diesen festgelegt ist, wie `Activity` in der folgenden Tabelle `type` `invoke` `name` `composeExtension` dargestellt.

Zusätzlich zu den Standardmäßigen Botaktivitätseigenschaften enthält die Nutzlast die folgenden Anforderungsmetadaten:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp; muss `invoke` sein. |
|`name`| Typ des Befehls, der für Ihren Dienst ausgegeben wird. Derzeit werden die folgenden Typen unterstützt: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal vorgenommen wurde). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal vorgenommen wurde). |
|`clientInfo`|Optionale Metadaten zur Clientsoftware, die zum Senden der Nachricht eines Benutzers verwendet wird. Die Entität kann zwei Eigenschaften enthalten:<br>Das Feld enthält den erkannten Speicherort `country` des Benutzers.<br>Das `platform` Feld beschreibt die Messagingclientplattform. <br>Weitere Informationen finden Sie *unter* [Non-IRI entity types — clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Die Anforderungsparameter selbst befinden sich im Value-Objekt, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des Befehls, der vom Benutzer aufgerufen wird und einem der befehle, die im App-Manifest deklariert sind, zustimmungen. |
| `parameters` | Array von Parametern. Jedes Parameterobjekt enthält den Parameternamen sowie den vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierungsparameter: <br>`skip`: Anzahl für diese Abfrage überspringen <br>`count`: Anzahl der zurückzukehrenden Elemente |

#### <a name="request-example"></a>Anforderungsbeispiel

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
    "type": "clientInfo",
      "country": "US",
      "platform": "Windows"
    }
  ]
}
```

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a>Empfangen von Anforderungen von Links, die in das Meldungsfeld verfassen eingefügt wurden

Als Alternative (oder zusätzlich) zum Durchsuchen Ihres externen Diensts können Sie eine in das Meldungsfeld verfassen eingefügte URL verwenden, um Ihren Dienst zu abfragen und eine Karte zurückzukehren. Im folgenden Screenshot hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingegeben, die die Messagingerweiterung in eine Karte aufgelöst hat.

![Beispiel für die Verknüpfungsentfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Damit Ihre Messagingerweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das Array zu Ihrem App-Manifest hinzufügen, wie `messageHandlers` im folgenden Beispiel gezeigt:

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

Nachdem Sie die Domäne zum Lauschen des App-Manifests hinzugefügt haben, [](#respond-to-user-requests) müssen Sie Ihren Botcode ändern, um auf die unten aufgeführte Aufrufanforderung zu reagieren.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Wenn Ihre App mehrere Elemente zurückgibt, wird nur das erste verwendet.

### <a name="respond-to-user-requests"></a>Reagieren auf Benutzeranforderungen

Wenn der Benutzer eine Abfrage ausführt, stellt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus. An diesem Punkt hat Ihr Code 5 Sekunden Zeit, um eine HTTP-Antwort auf die Anforderung zu senden. Während dieser Zeit kann Ihr Dienst zusätzliche Nachschlage- oder sonstige Geschäftslogik ausführen, die für die Anforderung erforderlich ist.

Ihr Dienst sollte mit den Ergebnissen antworten, die mit der Benutzerabfrage übereinstimmen. Die Antwort muss einen HTTP-Statuscode von und ein `200 OK` gültiges Application/json-Objekt mit dem folgenden Textkörper angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag auf oberster Ebene.|
|`composeExtension.type`|Antworttyp. Die folgenden Typen werden unterstützt: <br>`result`: zeigt eine Liste der Suchergebnisse an <br>`auth`: fordert den Benutzer zur Authentifizierung auf <br>`config`: fordert den Benutzer auf, die Messagingerweiterung einrichten <br>`message`: zeigt eine Nur-Text-Nachricht an. |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result` verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: ein Raster von Miniaturansichtsbildern |
|`composeExtension.attachments`|Array gültiger Anlagenobjekte. Wird für Antworten vom Typ `result` verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ oder `auth` `config` verwendet. |
|`composeExtension.text`|Meldung, die angezeigt werden soll. Wird für Antworten vom Typ `message` verwendet. |

#### <a name="response-card-types-and-previews"></a>Typen und Vorschauen von Antwortkarten

Wir unterstützen die folgenden Anlagentypen:

* [Miniaturansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Heldenkarte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Connector-Karte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Eine [Übersicht finden Sie unter Karten.](~/task-modules-and-cards/what-are-cards.md)

Informationen zur Verwendung der Miniaturansichts- und Heldenkartentypen finden Sie unter [Hinzufügen von Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)

Weitere Informationen zur Office 365 Connector-Karte finden Sie unter [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird in der Benutzeroberfläche von Microsoft Teams mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf zwei Arten generiert:

* Verwenden der `preview` Eigenschaft innerhalb des `attachment` Objekts. Die `preview` Anlage kann nur eine Hero- oder Miniaturansichtskarte sein.
* Extrahiert aus den grundlegenden `title` Eigenschaften , und der `text` `image` Anlage. Diese werden nur verwendet, wenn `preview` die Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.

Sie können eine Vorschau einer Adaptiven oder Office 365 Connector-Karte in der Ergebnisliste anzeigen, indem Sie einfach die Vorschaueigenschaft festlegen. dies ist nicht erforderlich, wenn es sich bei den Ergebnissen bereits um Hero- oder Miniaturansichtskarten handelt. Wenn Sie die Vorschauanlage verwenden, muss es sich entweder um eine Hero- oder Miniaturansichtskarte geben. Wenn keine Vorschaueigenschaft angegeben ist, wird bei der Vorschau der Karte ein Fehler angezeigt, und es wird nichts angezeigt.

#### <a name="response-example"></a>Anforderungsbeispiel

In diesem Beispiel wird eine Antwort mit zwei Ergebnissen gezeigt, bei der verschiedene Kartenformate gemischt werden: Office 365 Connector und Adaptive. Auch wenn Sie in Ihrer Antwort wahrscheinlich bei einem Kartenformat bleiben möchten, zeigt dies, wie die Eigenschaft jedes Elements in der Auflistung explizit eine Vorschau im Hero- oder Miniaturansichtsformat definieren muss, wie oben `preview` `attachments` beschrieben.

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
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
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

### <a name="default-query"></a>Standardabfrage

Wenn Sie im Manifest auf festlegen, gibt Microsoft Teams eine "Standardabfrage" aus, wenn der Benutzer die `initialRun` `true` Messagingerweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe von vorab aufgefüllten Ergebnissen reagieren. Dies kann z. B. nützlich sein, um zuletzt angezeigte Elemente, Favoriten oder andere Informationen, die nicht von benutzereingaben abhängig sind, angezeigt zu werden.

Die Standardabfrage hat dieselbe Struktur wie jede normale Benutzerabfrage, mit Ausnahme eines Parameters, `initialRun` dessen Zeichenfolgenwert `true` ist .

#### <a name="request-example-for-a-default-query"></a>Anforderungsbeispiel für eine Standardabfrage

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

## <a name="identify-the-user"></a>Identifizieren des Benutzers

Jede Anforderung an Ihre Dienste enthält die verschleierte ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory-Objekt-ID.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die `id` Werte und sind garantiert der des `aadObjectId` authentifizierten Teams-Benutzers. Sie können als Schlüssel verwendet werden, um Anmeldeinformationen oder einen beliebigen zwischengespeicherten Status in Ihrem Dienst nach zu suchen. Darüber hinaus enthält jede Anforderung die Azure Active Directory-Mandanten-ID des Benutzers, mit der die Organisation des Benutzers identifiziert werden kann. Falls zutreffend, enthält die Anforderung auch die Team- und Kanal-IDs, von denen die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messagingerweiterung verwenden kann. Wenn Sie einen Bot oder eine Registerkarte geschrieben haben, die sich im Benutzer signiert, sollte dieser Abschnitt vertraut sein.

Die Reihenfolge lautet wie folgt:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.
2. Ihr Dienst überprüft, ob sich der Benutzer zuerst authentifiziert hat, indem er die Teams-Benutzer-ID überprüft.
3. Wenn sich der Benutzer nicht authentifiziert hat, senden Sie eine Antwort mit einer vorgeschlagenen `auth` `openUrl` Aktion zurück, einschließlich der Authentifizierungs-URL.
4. Der Microsoft Teams-Client startet ein Popupfenster, in dem Ihre Webseite mit der angegebenen Authentifizierungs-URL hosten wird.
5. Nach der Anmeldung des Benutzers sollten Sie ihr Fenster schließen und einen "Authentifizierungscode" an den Teams-Client senden.
6. Der Teams-Client gibt die Abfrage dann erneut an Ihren Dienst weiter, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 entspricht. Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu schädlich zu machen. Dadurch wird die Schleife geschlossen, um die sichere Authentifizierungssequenz zu beenden.

### <a name="respond-with-a-sign-in-action"></a>Reagieren mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung auffordert, antworten Sie mit einer vorgeschlagenen Aktion vom Typ, die `openUrl` die Authentifizierungs-URL enthält.

#### <a name="response-example-for-a-sign-in-action"></a>Antwortbeispiel für eine Anmeldeaktion

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
> Damit die Anmeldeerfahrung in einem Teams-Popup gehostet wird, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden. (Siehe [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschema.)

### <a name="start-the-sign-in-flow"></a>Starten des Anmeldeflusses

Ihre Anmeldeerfahrung sollte reaktionsfähig sein und in ein Popupfenster passen. Es sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübertragung verwendet.

Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams ausgeführt werden, muss Ihr Code im Fenster zuerst `microsoftTeams.initialize()` aufrufen. Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Teams-Benutzer-ID an Ihr Fenster übergeben, die sie dann an die OAuth-Anmelde-URL übergeben kann.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmeldeflusses

Wenn die Anmeldeanforderung abgeschlossen ist und wieder zu Ihrer Seite umgeleitet wird, sollten sie die folgenden Schritte ausführen:

1. Generieren Sie einen Sicherheitscode. (Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst zusammen mit den Anmeldeinformationen zwischenspeichern, die über den Anmeldefluss (z. B. OAuth 2.0-Token) erhalten wurden.
2. Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode auf, und übergeben Sie ihn.

An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams-Client übergeben. Der Client kann nun die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der Eigenschaft erneut `state` ausführen. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nach zu suchen, um die Authentifizierungssequenz zu vervollständigen und dann die Benutzeranforderung zu vervollständigen.

#### <a name="reissued-request-example"></a>Beispiel für neu ausgestellte Anforderung

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
        "type": "clientInfo",
        "country": "US",
        "platform": "Web",
        
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

## <a name="sdk-support"></a>SDK-Unterstützung

### <a name="net"></a>.NET

Zum Empfangen und Behandeln von Abfragen mit dem Bot Builder SDK für .NET können Sie den Aktionstyp für die eingehende Aktivität überprüfen und dann die Hilfsmethode im `invoke` NuGet-Paket [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) verwenden, um zu ermitteln, ob es sich um eine Messagingerweiterungsaktivität handeln soll.

#### <a name="example-code-in-net"></a>Beispielcode in .NET

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

### <a name="nodejs"></a>Node.js

#### <a name="example-code-in-nodejs"></a>Beispielcode in Node.js

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
*Siehe auch* [Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
