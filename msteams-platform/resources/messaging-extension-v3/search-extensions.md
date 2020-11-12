---
title: Suche mit Messaging Erweiterungen
description: Beschreibt, wie suchbasierte Messaging Erweiterungen entwickelt werden
keywords: Microsoft Teams Messaging Extensions Messaging Extensions Search
ms.date: 07/20/2019
ms.openlocfilehash: f46548d2e7e03ecebd8bc0fb6685aeb82b8eec6e
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "48998000"
---
# <a name="search-with-messaging-extensions"></a>Suche mit Messaging Erweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Suchbasierte Messaging-Erweiterungen ermöglichen es Ihnen, ihren Dienst abzufragen und diese Informationen in Form einer Karte nach rechts in Ihre Nachricht einzusenden.

![Beispiel für eine Messaging Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird die Vorgehensweise beschrieben.

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="search-type-message-extensions"></a>Nachrichten Erweiterungen für Such Typen

Legen Sie für die suchbasierte Messaging Erweiterung den `type` Parameter auf fest `query` . Unten sehen Sie ein Beispiel für ein Manifest mit einem einzigen Suchbefehl. Einer einzelnen Messaging Erweiterung können bis zu 10 verschiedene Befehle zugeordnet werden. Dies kann sowohl mehrere Suchfunktionen als auch mehrere Aktionsbasierte Befehle umfassen.

#### <a name="complete-app-manifest-example"></a>Beispiel für ein vollständiges App-Manifest

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

### <a name="test-via-uploading"></a>Testen über hochladen

Sie können Ihre Messaging Erweiterung testen, indem Sie Ihre APP hochladen.

Um Ihre Messaging Erweiterung zu öffnen, navigieren Sie zu einem beliebigen Chat oder Kanal. Wählen Sie im Feld Verfassen die Schaltfläche **Weitere Optionen** ( **&#8943;** ) aus, und wählen Sie Ihre Messaging Erweiterung aus.

## <a name="add-event-handlers"></a>Hinzufügen von Ereignishandlern

Der Großteil ihrer Arbeit umfasst das `onQuery` Ereignis, das alle Interaktionen im Fenster Messaging Erweiterung verarbeitet.

Wenn Sie `canUpdateConfiguration` `true` im Manifest auf festlegen, aktivieren Sie das Menüelement **Einstellungen** für Ihre Messaging Erweiterung und müssen auch verarbeiten `onQuerySettingsUrl` und `onSettingsUpdate` .

### <a name="handle-onquery-events"></a>Behandeln von onquery-Ereignissen

Eine Messaging Erweiterung empfängt ein `onQuery` Ereignis, wenn im Fenster Messaging Erweiterung etwas passiert oder an das Fenster gesendet wird.

Wenn Ihre Messaging-Erweiterung eine Konfigurationsseite verwendet, sollte Ihr Handler `onQuery` zunächst auf gespeicherte Konfigurationsinformationen überprüfen; wenn die Messaging Erweiterung nicht konfiguriert ist, geben Sie eine `config` Antwort mit einem Link zur Konfigurationsseite zurück. Beachten Sie, dass die Antwort von der Konfigurationsseite auch von behandelt wird `onQuery` . (Die einzige Ausnahme ist, wenn die Konfigurationsseite vom Handler für aufgerufen wird `onQuerySettingsUrl` ; Lesen Sie den folgenden Abschnitt.)

Wenn Ihre Messaging-Erweiterung Authentifizierung erfordert, überprüfen Sie die Benutzerstatusinformationen; Wenn der Benutzer nicht angemeldet ist, befolgen Sie die Anweisungen im Abschnitt [Authentifizierung](#authentication) weiter unten in diesem Thema.

Überprüfen Sie als nächstes, ob `initialRun` festgelegt ist, und führen Sie in diesem Fall entsprechende Maßnahmen durch, beispielsweise die Bereitstellung von Anweisungen oder eine Liste von Antworten.

Der Rest Ihres Handlers `onQuery` fordert den Benutzer zur Eingabe von Informationen auf, zeigt eine Liste mit Vorschau Karten an und gibt die vom Benutzer ausgewählte Karte zurück.

### <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Behandeln von onQuerySettingsUrl-und onSettingsUpdate-Ereignissen

Die `onQuerySettingsUrl` -und- `onSettingsUpdate` Ereignisse werden zusammenarbeiten, um das Menüelement **Einstellungen** zu aktivieren.

![Screenshots des Menüelements "Speicherorte von Einstellungen"](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

Der Handler für `onQuerySettingsUrl` gibt die URL für die Konfigurationsseite zurück, nachdem die Konfigurationsseite geschlossen wurde, der Handler für `onSettingsUpdate` akzeptiert und speichert den zurückgegebenen Zustand. (Dies ist der einzige Fall, in dem `onQuery` die Antwort wird *nicht* von der Konfigurationsseite empfangen.)

## <a name="receive-and-respond-to-queries"></a>Empfangen und beantworten von Abfragen

Jede Anforderung an Ihre Messaging Erweiterung erfolgt über ein `Activity` Objekt, das an die Rückruf-URL gesendet wird. Die Anforderung enthält Informationen zum Benutzer Befehl wie ID und Parameterwerte. Die Anforderung liefert auch Metadaten zu dem Kontext, in dem Ihre Erweiterung aufgerufen wurde, einschließlich Benutzer-und Mandanten-ID sowie Chat-ID oder Kanal-und Team-IDs.

### <a name="receive-user-requests"></a>Empfangen von Benutzeranforderungen

Wenn ein Benutzer eine Abfrage ausführt, sendet Microsoft Teams Ihrem Dienst ein Standardmäßiges bot-Framework `Activity` -Objekt. Ihr Dienst sollte seine Logik für einen ausführen, der `Activity` `type` auf `invoke` `name` einen unterstützten Typ festgelegt und festgelegt hat `composeExtension` , wie in der folgenden Tabelle dargestellt.

Zusätzlich zu den standardmäßigen bot-Aktivitätseigenschaften enthält die Nutzlast die folgenden Anforderungs Metadaten:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Typ der Anforderung; muss sein `invoke` . |
|`name`| Der Typ des Befehls, der für den Dienst ausgestellt wird. Derzeit werden die folgenden Typen unterstützt: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| Die ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Der Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`clientInfo`|Optionale Metadaten zur Client Software, die zum Senden der Nachricht eines Benutzers verwendet wurde. Die Entität kann zwei Eigenschaften enthalten:<br>Das `country` Feld enthält den erkannten Speicherort des Benutzers.<br>Das `platform` Feld beschreibt die Messaging-Clientplattform. <br>Weitere Informationen *finden Sie unter* [nicht-IRI-Entitätstypen – abgeschlossen werden ungültig](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Die Anforderungsparameter selbst werden im Value-Objekt gefunden, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht. |
| `parameters` | Array von Parametern. Jedes Parameter-Objekt enthält den Namen des Parameters sowie den vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierung Parameter: <br>`skip`: Skip count für diese Abfrage <br>`count`: Anzahl der zurückzugebenden Elemente |

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

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a>Empfangen von Anforderungen von Links, die in das Meldungsfeld "Verfassen" eingefügt werden

Alternativ (oder zusätzlich) zum Durchsuchen Ihres externen Diensts können Sie eine URL verwenden, die in das Meldungsfeld verfassen eingefügt wurde, um Ihren Dienst abzufragen und eine Karte zurückzugeben. Im Screenshot unten hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die von der Messaging Erweiterung in eine Karte aufgelöst wurde.

![Beispiel für eine Link-Entfaltung](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Damit Ihre Messaging Erweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array wie im folgenden Beispiel zu Ihrem App-Manifest hinzufügen:

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

Nachdem Sie die Domäne zum Überwachen des App-Manifests hinzugefügt haben, müssen Sie Ihren botcode so ändern, dass er auf die unten gezeigte Invoke-Anforderung [antwortet](#respond-to-user-requests) .

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Wenn Ihre APP mehrere Elemente zurückgibt, wird nur die erste verwendet.

### <a name="respond-to-user-requests"></a>Reagieren auf Benutzeranforderungen

Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone http-Anforderung an Ihren Dienst aus. An diesem Zeitpunkt hat der Code 5 Sekunden, um eine HTTP-Antwort auf die Anforderung bereitzustellen. Während dieser Zeit kann der Dienst zusätzliche Suchvorgänge durchführen oder eine andere Geschäftslogik, die für die Zustellung der Anforderung benötigt wird.

Ihr Dienst sollte mit den Ergebnissen Antworten, die mit der Benutzerabfrage übereinstimmen. Die Antwort muss einen HTTP-Statuscode `200 OK` und ein gültiges Application/JSON-Objekt mit folgendem Text angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag auf oberster Ebene.|
|`composeExtension.type`|Typ der Antwort. Die folgenden Typen werden unterstützt: <br>`result`: zeigt eine Liste der Suchergebnisse an. <br>`auth`: der Benutzer wird aufgefordert, sich zu authentifizieren. <br>`config`: der Benutzer wird aufgefordert, die Messaging Erweiterung einzurichten. <br>`message`: zeigt eine Nur-Text-Nachricht an. |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ verwendet `result` . <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: ein Raster von Miniaturbildern |
|`composeExtension.attachments`|Array gültiger Attachment-Objekte. Wird für Antworten vom Typ verwendet `result` . <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ `auth` oder verwendet `config` . |
|`composeExtension.text`|Anzuzeigende Meldung. Wird für Antworten vom Typ verwendet `message` . |

#### <a name="response-card-types-and-previews"></a>Antwortkarten Typen und-Vorschauen

Wir unterstützen die folgenden Anlagentypen:

* [Miniatur Ansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero Card](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Anschluss Karte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Eine Übersicht finden Sie unter [Cards](~/task-modules-and-cards/what-are-cards.md) .

Weitere Informationen zur Verwendung der Miniaturansicht-und Hero-Kartentypen finden Sie unter [Add Cards and Card Actions](~/task-modules-and-cards/cards/cards-actions.md).

Weitere Informationen zur Office 365-Verbindungskarte finden Sie unter [using Office 365 Connector Cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird auf der Microsoft Teams-Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf eine von zwei Arten generiert:

* Verwenden der `preview` -Eigenschaft innerhalb des- `attachment` Objekts. Die `preview` Anlage kann nur eine Hero-oder Thumbnail-Karte sein.
* Extrahiert aus den `title` Eigenschaften Basic, `text` und und der `image` Anlage. Diese werden nur verwendet, wenn die `preview` Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.

Sie können eine Vorschau einer adaptiven oder Office 365-connectorkarte in der Ergebnisliste anzeigen, indem Sie einfach die zugehörige Preview-Eigenschaft festlegen; Dies ist nicht erforderlich, wenn die Ergebnisse bereits Hero-oder Thumbnail-Karten sind. Wenn Sie die Vorschau Anlage verwenden, muss es sich entweder um eine Hero-oder eine Miniatur Ansichtskarte handeln. Wenn keine Preview-Eigenschaft angegeben wird, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.

#### <a name="response-example"></a>Anforderungsbeispiel

In diesem Beispiel wird eine Antwort mit zwei Ergebnissen gezeigt, wobei unterschiedliche Kartenformate gemischt werden: Office 365-Konnektor und adaptiv. Während Sie wahrscheinlich mit einem Kartenformat in ihrer Antwort bleiben möchten, wird gezeigt, wie die `preview` Eigenschaft der einzelnen Elemente in der `attachments` Auflistung explizit eine Vorschau im Hero-oder Miniatur Ansichtsformat definieren muss, wie oben beschrieben.

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

### <a name="default-query"></a>Standardabfrage

Wenn Sie `initialRun` `true` im Manifest auf festlegen, gibt Microsoft Teams eine "Standard"-Abfrage aus, wenn der Benutzer die Messaging Erweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe von vorab aufgefüllten Ergebnissen Antworten. Dies kann hilfreich sein, um beispielsweise kürzlich angezeigte Elemente, Favoriten oder andere Informationen anzuzeigen, die nicht von der Benutzereingabe abhängig sind.

Die Standardabfrage hat dieselbe Struktur wie jede reguläre Benutzerabfrage, mit Ausnahme eines Parameters, `initialRun` dessen Zeichenfolgenwert ist `true` .

#### <a name="request-example-for-a-default-query"></a>Anforderungs Beispiel für eine Standardabfrage

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

Jede Anforderung an ihre Dienste umfasst die verborgene ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory Objekt-ID.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die `id` `aadObjectId` Werte und sind garantiert die des authentifizierten Teams-Benutzers. Sie können als Schlüssel zum Nachschlagen von Anmeldeinformationen oder einem beliebigen zwischengespeicherten Zustand in Ihrem Dienst verwendet werden. Darüber hinaus enthält jede Anforderung die Azure Active Directory Mandanten-ID des Benutzers, die zum Identifizieren der Organisation des Benutzers verwendet werden kann. Wenn zutreffend, enthält die Anforderung auch die Team-und Kanal-IDs, aus denen die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messaging Erweiterung verwenden kann. Wenn Sie einen bot oder eine Registerkarte geschrieben haben, die den Benutzer signiert, sollte dieser Abschnitt vertraut sein.

Die Sequenz lautet wie folgt:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an den Dienst gesendet.
2. Der Dienst überprüft, ob der Benutzer zuerst authentifiziert wurde, indem er die Benutzer-ID des Teams überprüft.
3. Wenn der Benutzer nicht authentifiziert wurde, senden Sie eine `auth` Antwort mit einer `openUrl` vorgeschlagenen Aktion einschließlich der Authentifizierungs-URL zurück.
4. Der Microsoft Teams-Client startet ein Popupfenster, das Ihre Webseite unter Verwendung der angegebenen Authentifizierungs-URL hostet.
5. Nachdem sich der Benutzer angemeldet hat, sollten Sie das Fenster schließen und einen "Authentifizierungscode" an den Microsoft Teams-Client senden.
6. Der Microsoft Teams-Client gibt dann die Abfrage erneut an Ihren Dienst aus, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem in Schritt 5 übereinstimmt. Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmelde Ablauf vorzutäuschen oder zu gefährden. Dies effektiv "schließt die Schleife", um die sichere Authentifizierungssequenz abzuschließen.

### <a name="respond-with-a-sign-in-action"></a>Reagieren mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, Antworten Sie mit einer vorgeschlagenen Aktion vom Typ `openUrl` , die die Authentifizierungs-URL enthält.

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
> Damit die Anmelde Umgebung in einem Teams-Popup gehostet werden kann, muss der Domänenteil der URL in der Liste der gültigen Domänen in Ihrer APP aufgeführt sein. (Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifest-Schema.)

### <a name="start-the-sign-in-flow"></a>Starten des Anmelde Flusses

Ihre Anmelde Erfahrung sollte reagieren und in ein Popupfenster passt. Sie sollte in das [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübergabe verwendet.

Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams durchführen, muss der Code im Fenster zuerst aufgerufen werden `microsoftTeams.initialize()` . Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Benutzer-ID des Teams an das Fenster übergeben, das dann an die OAuth-Anmelde-URL übergeben werden kann.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmelde Flusses

Wenn die Anmeldeanforderung abgeschlossen wird und zu Ihrer Seite zurückgeleitet wird, sollten Sie die folgenden Schritte ausführen:

1. Generieren Sie einen Sicherheitscode. (Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst Zwischenspeichern, zusammen mit den Anmeldeinformationen, die über den Anmelde Fluss abgerufen werden (beispielsweise OAuth 2,0-Token).
2. Rufen Sie `microsoftTeams.authentication.notifySuccess` den Sicherheitscode an, und übergeben Sie ihn.

Zu diesem Zeitpunkt wird das Fenster geschlossen, und die Steuerung wird an den Microsoft Teams-Client übergeben. Der Client kann jetzt die ursprüngliche Benutzerabfrage erneut ausgeben, zusammen mit dem Sicherheitscode in der `state` -Eigenschaft. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.

#### <a name="reissued-request-example"></a>Beispiel für eine erneut aufgegebene Anforderung

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

Wenn Sie Abfragen mit dem bot Builder SDK für .net empfangen und verarbeiten möchten, können Sie den `invoke` Aktionstyp für die eingehende Aktivität überprüfen und dann die Hilfsmethode im NuGet-Paket " [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) " verwenden, um zu ermitteln, ob es sich um eine Messaging Erweiterungs Aktivität handelt.

#### <a name="example-code-in-net"></a>Beispielcode in .net

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
*Siehe auch* [bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
