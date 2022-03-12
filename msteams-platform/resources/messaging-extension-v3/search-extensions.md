---
title: Suchen mit Messaging-Erweiterungen
description: Beschreibt, wie suchbasierte Messaging-Erweiterungen entwickelt werden
keywords: Messaging-Erweiterungen für Teams – Suche nach Messaging-Erweiterungen
ms.topic: how-to
ms.localizationpriority: medium
ms.date: 07/20/2019
ms.openlocfilehash: dca01a22d4479d1f7c59689c5321483371c4aff2
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453712"
---
# <a name="search-with-messaging-extensions"></a>Suchen mit Messaging-Erweiterungen

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Suchbasierte Messaging-Erweiterungen ermöglichen es Ihnen, Ihren Dienst abfragt und diese Informationen in Form einer Karte direkt in Ihrer Nachricht zu posten.

![Beispiel für eine Messaging-Erweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

In den folgenden Abschnitten wird dies beschrieben:

[!include[common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

## <a name="search-type-message-extensions"></a>Suchtyp-Nachrichtenerweiterungen

Legen Sie für suchbasierte Messaging-Erweiterung den `type` Parameter auf `query`. Unten sehen Sie ein Beispiel für ein Manifest mit einem einzigen Suchbefehl. Einer einzelnen Messaging-Erweiterung können bis zu 10 verschiedene Befehle zugeordnet sein. Dies kann sowohl mehrere Suchbefehle als auch mehrere aktionsbasierte Befehle umfassen.

### <a name="complete-app-manifest-example"></a>Beispiel für ein vollständiges App-Manifest

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

## <a name="test-via-uploading"></a>Testen per Upload

Sie können Ihre Messaging-Erweiterung testen, indem Sie Ihre App hochladen.

Um Ihre Messaging-Erweiterung zu öffnen, navigieren Sie zu einem Ihrer Chats oder Kanäle. Wählen Sie im Feld "Verfassen" die Schaltfläche **"Weitere Optionen** " (**&#8943;**) aus, und wählen Sie Ihre Messaging-Erweiterung aus.

## <a name="add-event-handlers"></a>Hinzufügen von Ereignishandlern

Der Großteil Ihrer Arbeit umfasst das `onQuery` Ereignis, das alle Interaktionen im Messaging-Erweiterungsfenster verarbeitet.

Wenn Sie dies im Manifest festlegen `canUpdateConfiguration` `true`, aktivieren Sie das **Einstellungen** Menüelement für Ihre Messaging-Erweiterung und müssen auch behandeln `onQuerySettingsUrl` und `onSettingsUpdate`.

## <a name="handle-onquery-events"></a>Behandeln von onQuery-Ereignissen

Eine Messaging-Erweiterung empfängt ein `onQuery` Ereignis, wenn im Messaging-Erweiterungsfenster etwas passiert oder an das Fenster gesendet wird.

Wenn Ihre Messaging-Erweiterung eine Konfigurationsseite verwendet, sollte ihr Handler `onQuery` zunächst nach gespeicherten Konfigurationsinformationen suchen. Wenn die Messaging-Erweiterung nicht konfiguriert ist, geben Sie eine `config` Antwort mit einem Link zu Ihrer Konfigurationsseite zurück. Beachten Sie, dass die Antwort von der Konfigurationsseite auch von `onQuery`behandelt wird. Die einzige Ausnahme ist, wenn die Konfigurationsseite vom Handler `onQuerySettingsUrl`aufgerufen wird. Weitere Informationen finden Sie im folgenden Abschnitt:

Wenn Ihre Messaging-Erweiterung eine Authentifizierung erfordert, überprüfen Sie die Benutzerstatusinformationen. Wenn der Benutzer nicht angemeldet ist, befolgen Sie die Anweisungen im Abschnitt ["Authentifizierung"](#authentication) weiter unten in diesem Thema.

Überprüfen Sie als Nächstes, ob `initialRun` sie festgelegt ist. Falls ja, ergreifen Sie entsprechende Maßnahmen, z. B. das Bereitstellen von Anweisungen oder eine Liste von Antworten.

Der restliche Handler fordert `onQuery` den Benutzer zur Eingabe von Informationen auf, zeigt eine Liste der Vorschaukarten an und gibt die vom Benutzer ausgewählte Karte zurück.

## <a name="handle-onquerysettingsurl-and-onsettingsupdate-events"></a>Behandeln von onQuerySettingsUrl- und onSettingsUpdate-Ereignissen

Die Ereignisse und ereignisse arbeiten zusammen, um das **Einstellungen** Menüelement zu aktivieren.`onQuerySettingsUrl` `onSettingsUpdate`

![Screenshots der Speicherorte Einstellungen Menüelements](~/assets/images/compose-extensions/compose-extension-settings-menu-item.png)

Der Handler für `onQuerySettingsUrl` gibt die URL für die Konfigurationsseite zurück. Nachdem die Konfigurationsseite geschlossen wurde, akzeptiert ihr Handler den `onSettingsUpdate` zurückgegebenen Zustand und speichert den zurückgegebenen Zustand. Dies ist der Fall, in dem `onQuery` die Antwort von der Konfigurationsseite *nicht* empfangen wird.

## <a name="receive-and-respond-to-queries"></a>Empfangen und Beantworten von Abfragen

Jede Anforderung an Ihre Messaging-Erweiterung erfolgt über ein `Activity` Objekt, das in Ihrer Rückruf-URL bereitgestellt wird. Die Anforderung enthält Informationen zum Benutzerbefehl, z. B. ID- und Parameterwerte. Die Anforderung liefert auch Metadaten über den Kontext, in dem Ihre Erweiterung aufgerufen wurde, einschließlich Benutzer- und Mandanten-ID, sowie Chat-ID oder Kanal- und Team-IDs.

### <a name="receive-user-requests"></a>Empfangen von Benutzeranforderungen

Wenn ein Benutzer eine Abfrage durchführt, sendet Microsoft Teams Ihrem Dienst ein standardmäßiges Bot Framework-Objekt`Activity`. Der Dienst sollte seine Logik für einen `Activity` Typ ausführen, der auf `invoke` einen unterstützten `composeExtension` Typ festgelegt und `name` auf diesen festgelegt wurde`type`, wie in der folgenden Tabelle dargestellt.

Zusätzlich zu den standardmäßigen Bot-Aktivitätseigenschaften enthält die Nutzlast die folgenden Anforderungsmetadaten:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp; `invoke`muss . |
|`name`| Typ des Befehls, der an Ihren Dienst ausgegeben wird. Derzeit werden die folgenden Typen unterstützt: <br>`composeExtension/query` <br>`composeExtension/querySettingUrl` <br>`composeExtension/setting` <br>`composeExtension/selectItem` <br>`composeExtension/queryLink` |
|`from.id`| DIE ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Microsoft Azure Active Directory (Azure AD) Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Microsoft Azure Active Directory (Azure AD) Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal vorgenommen wurde). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal vorgenommen wurde). |
|`clientInfo`|Optionale Metadaten über die Clientsoftware, die zum Senden der Nachricht eines Benutzers verwendet wird. Die Entität kann zwei Eigenschaften enthalten:<br>Das `country` Feld enthält den vom Benutzer erkannten Speicherort.<br>Das `platform` Feld beschreibt die Messaging-Clientplattform. <br>Weitere Informationen *finden Sie unter* [Nicht-IRI-Entitätstypen – clientInfo](https://github.com/microsoft/botframework-sdk/blob/master/specs/botframework-activity/botframework-activity.md#clientinfo).|

Die Anforderungsparameter selbst befinden sich im Wertobjekt, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht. |
| `parameters` | Array von Parametern: Jedes Parameterobjekt enthält den Parameternamen sowie den vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierungsparameter: <br>`skip`: Anzahl für diese Abfrage überspringen <br>`count`: Anzahl der zurückzugebenden Elemente |

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

### <a name="receive-requests-from-links-inserted-into-the-compose-message-box"></a>Empfangen von Anforderungen von Links, die in das Feld zum Verfassen von Nachrichten eingefügt wurden

Als Alternative (oder zusätzlich) zum Durchsuchen Ihres externen Diensts können Sie eine URL verwenden, die in das Feld zum Verfassen von Nachrichten eingefügt wurde, um Ihren Dienst abfragt und eine Karte zurückzugeben. Im folgenden Screenshot hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die die Messaging-Erweiterung in eine Karte aufgelöst hat.

![Beispiel für die Verbreitung von Links](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

Damit Ihre Messaging-Erweiterung auf diese Weise mit Links interagieren kann, müssen Sie zunächst das `messageHandlers` Array zu Ihrem App-Manifest hinzufügen, wie im folgenden Beispiel gezeigt:

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

Nachdem Sie die Domäne zum Überwachen des App-Manifests hinzugefügt haben, müssen Sie Ihren Botcode ändern, um auf die folgende Aufrufanforderung zu [reagieren](#respond-to-user-requests) .

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Wenn Ihre App mehrere Elemente zurückgibt, wird nur das erste Element verwendet.

### <a name="respond-to-user-requests"></a>Antworten auf Benutzeranforderungen

Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus. An diesem Punkt hat Ihr Code 5 Sekunden Zeit, um eine HTTP-Antwort auf die Anforderung bereitzustellen. Während dieser Zeit kann Ihr Dienst zusätzliche Nachschlagevorgänge oder eine beliebige andere Geschäftslogik ausführen, die für die Bearbeitung der Anforderung erforderlich ist.

Ihr Dienst sollte mit den Ergebnissen antworten, die mit der Benutzerabfrage übereinstimmen. Die Antwort muss einen HTTP-Statuscode und ein gültiges `200 OK` Application/json-Objekt mit dem folgenden Text angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag auf oberster Ebene.|
|`composeExtension.type`|Antworttyp. Die folgenden Typen werden unterstützt: <br>`result`: zeigt eine Liste der Suchergebnisse an <br>`auth`: fordert den Benutzer zur Authentifizierung auf <br>`config`: fordert den Benutzer auf, die Messaging-Erweiterung einzurichten <br>`message`: zeigt eine Nur-Text-Nachricht an. |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: ein Raster mit Miniaturansichten |
|`composeExtension.attachments`|Array gültiger Anlagenobjekte. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ `auth` oder `config`verwendet. |
|`composeExtension.text`|Anzuzeigende Meldung. Wird für Antworten vom Typ `message`verwendet. |

#### <a name="response-card-types-and-previews"></a>Antwortkartentypen und Vorschauen

Wir unterstützen die folgenden Anlagentypen:

* [Miniaturbildkarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Weitere Informationen finden Sie unter [Karten](~/task-modules-and-cards/what-are-cards.md) für eine Übersicht.

Informationen zur Verwendung der Miniaturansicht- und Herokartentypen finden [Sie unter Hinzufügen von Karten und Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).

Weitere Dokumentationen zur Office 365 Connectorkarte finden Sie unter [Verwenden Office 365 Connectorkarten](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird auf der Microsoft Teams Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf zwei Arten generiert:

* Verwenden der `preview` Eigenschaft innerhalb des `attachment` Objekts. Die `preview` Anlage kann nur eine Hero- oder Miniaturansichtskarte sein.
* Extrahiert aus den grundlegenden `title`, `text`und `image` Eigenschaften der Anlage. Diese werden nur verwendet, wenn die `preview` Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.

Sie können eine Vorschau einer adaptiven oder Office 365 Connector-Karte in der Ergebnisliste anzeigen, indem Sie einfach die Vorschaueigenschaft festlegen. Dies ist nicht erforderlich, wenn die Ergebnisse bereits Favoriten- oder Miniaturansichtskarten sind. Wenn Sie die Vorschauanlage verwenden, muss es sich entweder um eine Hero- oder eine Miniaturansichtskarte handeln. Wenn keine Vorschaueigenschaft angegeben ist, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.

#### <a name="response-example"></a>Anforderungsbeispiel

Dieses Beispiel zeigt eine Antwort mit zwei Ergebnissen, wobei verschiedene Kartenformate gemischt werden: Office 365 Connector und Adaptive. Während Sie wahrscheinlich bei einem Kartenformat in Ihrer Antwort bleiben möchten, wird gezeigt, wie die `preview` Eigenschaft jedes Elements in der `attachments` Sammlung explizit eine Vorschau im Hero- oder Miniaturansichtsformat definieren muss, wie oben beschrieben.

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

Wenn Sie dies im Manifest festlegen `initialRun` `true`, gibt Microsoft Teams eine Standardabfrage aus, wenn der Benutzer die Messaging-Erweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe vorab ausgefüllter Ergebnisse antworten. Dies kann nützlich sein, um beispielsweise zuletzt angezeigte Elemente, Favoriten oder andere Informationen anzuzeigen, die nicht von benutzereingaben abhängig sind.

Die Standardabfrage weist die gleiche Struktur wie jede normale Benutzerabfrage auf, mit Ausnahme eines Parameters `initialRun` , dessen Zeichenfolgenwert lautet `true`.

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

Jede Anforderung an Ihre Dienste enthält die verborgene ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen und die Microsoft Azure Active Directory (Azure AD)-Objekt-ID des Benutzers.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die `id` Werte sind `aadObjectId` garantiert die des authentifizierten Teams Benutzers. Sie können als Schlüssel zum Nachschlagen von Anmeldeinformationen oder eines zwischengespeicherten Status in Ihrem Dienst verwendet werden. Darüber hinaus enthält jede Anforderung die Microsoft Azure Active Directory (Azure AD)-Mandanten-ID des Benutzers, die verwendet werden kann, um die Organisation des Benutzers zu identifizieren. Falls zutreffend, enthält die Anforderung auch die Team- und Kanal-IDs, von denen die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messaging-Erweiterung verwenden kann. Wenn Sie einen Bot oder eine Registerkarte geschrieben haben, die sich beim Benutzer anmeldet, sollte dieser Abschnitt vertraut sein.

Die Sequenz sieht wie folgt aus:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.
2. Ihr Dienst überprüft, ob der Benutzer sich zuerst authentifiziert hat, indem er die Teams Benutzer-ID überprüft.
3. Wenn sich der Benutzer nicht authentifiziert hat, senden Sie eine `auth` Antwort mit einer `openUrl` vorgeschlagenen Aktion einschließlich der Authentifizierungs-URL zurück.
4. Der Microsoft Teams-Client startet ein Popupfenster, in dem Ihre Webseite mithilfe der angegebenen Authentifizierungs-URL gehostet wird.
5. Nachdem sich der Benutzer angemeldet hat, sollten Sie ihr Fenster schließen und einen "Authentifizierungscode" an den Teams-Client senden.
6. Der Teams-Client sendet dann die Abfrage erneut an Ihren Dienst, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 übereinstimmt. Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu kompromittieren. Dadurch wird die Schleife "geschlossen", um die sichere Authentifizierungssequenz abzuschließen.

### <a name="respond-with-a-sign-in-action"></a>Antworten mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, antworten Sie mit einer vorgeschlagenen Aktion vom Typ `openUrl` , die die Authentifizierungs-URL enthält.

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
> Damit die Anmeldeumgebung in einem Teams Popup gehostet werden kann, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden. Weitere Informationen finden Sie unter ["validDomains](~/resources/schema/manifest-schema.md#validdomains) " im Manifestschema.

### <a name="start-the-sign-in-flow"></a>Starten des Anmeldeflusses

Ihre Anmeldeerfahrung sollte reaktionsfähig sein und in ein Popupfenster passen. Es sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) integriert werden, das die Nachrichtenübergabe verwendet.

Wie bei anderen eingebetteten Oberflächen, die in Microsoft Teams ausgeführt werden, muss Ihr Code innerhalb des Fensters zuerst aufgerufen werden`microsoftTeams.initialize()`. Wenn Ihr Code einen OAuth-Fluss durchführt, können Sie die Teams-Benutzer-ID an Ihr Fenster übergeben, die sie dann an die OAuth-Anmelde-URL übergeben kann.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmeldeflusses

Wenn die Anmeldeanforderung abgeschlossen ist und zurück zu Ihrer Seite geleitet wird, sollten die folgenden Schritte ausgeführt werden:

1. Generieren Sie einen Sicherheitscode. (Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst zusammen mit den Anmeldeinformationen zwischenspeichern, die über den Anmeldefluss abgerufen werden, z. B. OAuth 2.0-Token.
2. Rufen Sie den Sicherheitscode auf `microsoftTeams.authentication.notifySuccess` , und übergeben Sie ihn.

An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams Client übergeben. Der Client kann jetzt die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der `state` Eigenschaft erneut ausführen. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.

#### <a name="reissued-request-example"></a>Beispiel für erneutesued-Anforderung

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

Um Abfragen mit dem Bot Builder SDK für .NET zu empfangen und zu verarbeiten, können Sie nach dem `invoke` Aktionstyp für die eingehende Aktivität suchen und dann die Hilfsmethode im [NuGet-Pakets "Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)" verwenden, um zu ermitteln, ob es sich um eine Messaging-Erweiterung handelt.

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

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
