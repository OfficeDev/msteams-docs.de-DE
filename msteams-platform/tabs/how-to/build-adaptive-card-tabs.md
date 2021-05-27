---
title: Erstellen adaptiver Kartenregisterkarten
author: KirtiPereira
description: Erstellen von Registerkarten mit adaptiven Karten
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: d65fc537b5282c050d891a6a73ff114c630e2c1c
ms.sourcegitcommit: c59d90ae03eae32996db49f162855965b55c52fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2021
ms.locfileid: "52668848"
---
# <a name="build-tabs-with-adaptive-cards"></a>Erstellen von Registerkarten mit adaptiven Karten

> [!IMPORTANT]
> * Dieses Feature befindet sich im [öffentlichen Developer Preview](~/resources/dev-preview/developer-preview-intro.md) und wird auf Desktop- und Mobilgeräten unterstützt. Unterstützung im Webbrowser wird in Kürze verfügbar sein.
> * Registerkarten mit adaptiven Karten werden derzeit nur als persönliche Apps unterstützt.

Verwenden Sie adaptive Karten, um Registerkarten mühelos zu erstellen. Sie können Ihre Registerkarten mit fertigen Benutzeroberflächen-Lego-Blöcken erstellen, die auf Desktop, Web und Mobil nativ aussehen und sich als nativ anfühlen. Das Erstellen von Registerkarten mit adaptiven Karten zentralisiert alle Teams-App-Funktionen um ein Bot-Back-End und das Frontend adaptiver Karten, sodass kein anderes Back-End für Ihren Bot und Ihre Registerkarten benötigt wird. Dadurch werden die Server- und Wartungskosten Ihrer Teams erheblich reduziert. Dieser Artikel hilft Ihnen, die änderungen zu verstehen, die am App-Manifest vorgenommen werden müssen, wie die Aktivität aufgerufen wird und wie Informationen auf der Registerkarte mit adaptiven Karten aufgerufen werden, sowie die Auswirkungen auf den Workflow des Aufgabenmoduls. 

Die folgende Abbildung zeigt Buildregisterkarten mit adaptiven Karten auf Desktop- und Mobilgeräten: Beispiel für adaptive Karten, die :::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="in Registerkarten gerendert werden." border="false":::

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit der Verwendung adaptiver Karten zum Erstellen von Registerkarten beginnen, müssen Sie:

* Machen Sie sich mit [Bot-Entwicklung,](../../bots/what-are-bots.md) [adaptiven Karten](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)und [Aufgabenmodulen](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams.
* Sie können einen Bot in Teams Für Ihre Entwicklung ausführen.
* Be in [Public Developer Preview](~/resources/dev-preview/developer-preview-intro.md).

## <a name="changes-to-app-manifest"></a>Änderungen am App-Manifest

Persönliche Apps, die Registerkarten rendern, müssen ein `staticTabs` Array in ihr App-Manifest enthalten. Adaptive Kartenregisterkarten werden gerendert, wenn `contentBotId` die Eigenschaft in der Definition bereitgestellt `staticTab` wird. Statische Registerkartendefinitionen müssen entweder eine enthalten, die eine Adaptive Kartenregisterkarte oder eine , die eine typische gehostete Webinhaltsregisterkartenerfahrung `contentBotId` `contentUrl` an gibt.

> [!NOTE]
> Die `contentBotId` Eigenschaft ist derzeit manifest version 1.9 oder höher verfügbar. 

Geben Sie `contentBotId` der Eigenschaft die Eigenschaft `botId` an, mit der die Registerkarte Adaptive Karte kommunizieren muss. Die für die Registerkarte Adaptive Karte konfigurierte wird im Parameter jeder Aufrufanforderung gesendet und kann verwendet werden, um verschiedene adaptive Kartenregisterkarten zu unterscheiden, die vom gleichen Bot `entityId` `tabContext` unterstützt werden. Weitere Informationen zu anderen statischen Registerkartendefinitionsfeldern finden Sie unter [Manifestschema](../../resources/schema/manifest-schema.md#statictabs).

Im Folgenden finden Sie ein Beispielmanifest für adaptive Kartenregisterkarten:

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "1.9",
  "id": "00000000-0000-0000-0000-000000000000",
  "version": "0.0.1",
  "packageName": "acprototype",
  "developer": {
    "name": "Contoso",
    "websiteUrl": "https://contoso.yourwebsite.com",
    "privacyUrl": "https://contoso.yourwebsite.com/privacy.html",
    "termsOfUseUrl": "https://contoso.yourwebsite.com/terms.html"
  },
  "name": {
    "short": "Contoso",
    "full": "Contoso Home"
  },
  "description": {
    "short": "Add short description here",
    "full": "Add full description here"
  },
  "icons": {
    "outline": "icon-outline.png",
    "color": "icon-color.png"
  },
  "accentColor": "#D85028",
  "configurableTabs": [],
  "staticTabs": [
    {
      "entityId": "homeTab",
      "name": "Home",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    },
    {
      "entityId": "moreTab",
      "name": "More",
      "contentBotId": "00000000-0000-0000-0000-000000000000",
      "scopes": ["personal"]
    }
  ],
  "connectors": [],
  "composeExtensions": [],
  "permissions": ["identity", "messageTeamMembers"],
  "validDomains": [
    "contoso.yourwebsite.com",
    "token.botframework.com"
  ]
}
```

## <a name="invoke-activities"></a>Aufrufen von Aktivitäten

Die Kommunikation zwischen Ihrer Registerkarte für adaptive Karten und Ihrem Bot erfolgt über `invoke` Aktivitäten. Jede `invoke` Aktivität hat einen entsprechenden *Namen*. Verwenden Sie den Namen jeder Aktivität, um jede Anforderung zu unterscheiden. `tab/fetch` und `tab/submit` sind die aktivitäten, die in diesem Abschnitt behandelt werden.

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a>Abrufen der adaptiven Karte zum Rendern auf einer Registerkarte

`tab/fetch` ist die erste Aufrufanforderung, die Ihr Bot empfängt, wenn ein Benutzer eine Registerkarte für adaptive Karten öffnet. Wenn Ihr Bot die Anforderung empfängt, sendet er entweder eine Antwort **zur** Fortsetzung der Registerkarte oder eine Antwort der **Registerkartenauthentisierung.**
Die **Fortsetzungsantwort** enthält ein Array für **Karten**, das vertikal auf die Registerkarte in der Reihenfolge des Arrays gerendert wird.

> [!NOTE]
> Die **Antwort auf** die Authentifizierung wird im Abschnitt Authentifizierung [ausführlich](#authentication) erläutert.

Die folgenden Codeausschnitte sind Beispiele für `tab/fetch` Anforderung und Antwort:

**`tab/fetch` request**

```json
// tab/fetch POST request: agents/{botId}/invoke
{
    "name": "tab/fetch",
    "value: {
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        },
        "context": {
            "theme": "default"
            }
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}"
}
```

**`tab/fetch` response**

```json
// tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
                {
                    "card": adaptiveCard1,
                },
                {
                    "card": adaptiveCard2,
                }
                {
                    "card": adaptiveCard3
                }  
            ]
        },
    },
    "responseType": "tab"
}
```

### <a name="handle-submits-from-adaptive-card"></a>Behandeln von Übermittelten von adaptiver Karte

Nachdem eine adaptive Karte auf der Registerkarte gerendert wurde, muss sie in der Lage sein, auf Benutzerinteraktionen zu reagieren. Diese Antwort wird von der `tab/submit` Aufrufanforderung verarbeitet.

Wenn ein Benutzer auf der Registerkarte Adaptive Karte eine Schaltfläche auswählt, wird die Anforderung an Ihren Bot mit den entsprechenden Daten über die `tab/submit` *Action.Submit-Funktion* der adaptiven Karte ausgelöst. Die Adaptive Card-Daten sind über die Dateneigenschaft der Anforderung `tab/submit` verfügbar. Sie erhalten eine der folgenden Antworten auf Ihre Anforderung:

* Eine Http-Statuscodeantwort `200` ohne Text. Eine leere 200-Antwort führt zu keiner Aktion des Clients.
* Auf der `200` **Standardregisterkarte wird die** Antwort fortgesetzt, wie im Abschnitt ["Adaptive Karte abrufen"](#fetch-adaptive-card-to-render-to-a-tab) erläutert. Eine Antwort **für die Fortsetzung** der Registerkarte löst den Client aus, um die gerenderte Adaptive Kartenregisterkarte mit den adaptiven Karten im Kartenarray der Fortsetzungsantwort **zu** aktualisieren.

Die folgenden Codeausschnitte sind Beispiele für `tab/submit` Anforderung und Antwort:

**`tab/submit` request**

```json
// tab/submit POST request: agents/{botId}/invoke:
{
    "name": "tab/submit",
    "value": {
        "data": {
            "type": "tab/submit",
            //...<data properties>
            },
        "context": {
            "theme": "default"
            },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
            },
        },
    "conversation": {
           "id": "{generated_conversation_id}" 
        },
    "imdisplayname": "{user_display_name}"
}
```

**`tab/submit` response**

```json
//tab/fetch **continue** POST response:
{
    "tab": {
        "type": "continue",
        "value": {
            "cards": [
              {
                "card": adaptiveCard1,
                },
              {
                "card": adaptiveCard2,
                } 
            ]
        },
    },
    "responseType": "tab"
}
```

## <a name="understand-task-module-workflow"></a>Verstehen des Aufgabenmodulworkflows

Das Aufgabenmodul verwendet auch adaptive Karte zum Aufrufen und `task/fetch` Zum Aufrufen von Anforderungen und `task/submit` Antworten. Weitere Informationen finden Sie unter [Using Task Modules in Microsoft Teams bots](../../task-modules-and-cards/task-modules/task-modules-bots.md).

Mit der Einführung der Registerkarte Adaptive Karte ändert sich jedoch, wie der Bot auf eine Anforderung `task/submit` reagiert. Wenn Sie eine Registerkarte für adaptive Karten verwenden, antwortet der Bot auf die Aufrufanforderung mit der Standard-Tab-Continue-Antwort und schließt `task/submit` das Aufgabenmodul.  Die Registerkarte Adaptive Karte wird aktualisiert, indem die neue Liste der Im Antworttext der Registerkarte **"Fortsetzung"** bereitgestellten Karten gerendert wird.

### <a name="invoke-taskfetch"></a>Invoke `task/fetch`

Die folgenden Codeausschnitte sind Beispiele für `task/fetch` Anforderung und Antwort:

**`task/fetch` request**
```json
// task/fetch POST request: agents/{botId}/invoke
{
    "name": "task/fetch",
    "value": {
        "data": {
            "type": "task/fetch"
        },
        "context": {
            "theme": "default",
        },
        "tabContext": {
            "tabEntityId": "{tab_entity_id}"
        }
    },
    "imdisplayname": "{user_display_name}",
    "conversation": {
        "id": "{generated_conversation_id}"
    } 
}
```

**`task/fetch` response**

```json
// task/fetch POST response: agents/{botId}/invoke
{
    "task": {
        "value": {
            "title": "Ninja Cat",
            "height": "small",
            "width": "small",
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": adaptiveCard,
            }
        },
    "type": "continue"
    },
    "responseType": "task"
}
```

### <a name="invoke-tasksubmit"></a>Invoke `task/submit`

Die folgenden Codeausschnitte sind Beispiele für `task/submit` Anforderung und Antwort:

**`task/submit` request**

```json
// task/submit POST request: agent/{botId}/invoke:
{
    "name": "task/submit",
    "value": {
        "data": {serialized_data_object},
        "context": {
            "theme": "default"
        },
    "tabContext": {
        "tabEntityId": "{tab_entity_id}"
        },
    },
    "conversation": {
        "id": "{generated_conversation_id}"
    },
    "imdisplayname": "{user_display_name}",
}
```

**`task/submit` Antworttyp der Registerkarte**

```json
// tab/fetch **continue** POST response: 
{
    "task":{
        "value": {
            "tab": {
                "type": "continue",
                "value": {
                    "cards": [
                        {
                            "card": adaptiveCard1
                        },
                        {
                            "card": adaptiveCard2
                        }
                    ]
                }
            }
        },
        "type": "continue"
    },
    "responseType": "task"
}
```

## <a name="authentication"></a>Authentifizierung

In den vorherigen Abschnitten dieses Artikels haben Sie gesehen, dass die meisten Entwicklungsparadigmen aus den Aufgabenmodulanforderungen und -antworten in Registerkartenanforderungen und -antworten extrapoliert werden können. Beim Behandeln der Authentifizierung folgt der Workflow für adaptive Kartenregisterkarte jedoch dem Authentifizierungsmuster für Messagingerweiterungen. Weitere Informationen finden Sie unter [Hinzufügen der Authentifizierung](../../messaging-extensions/how-to/add-authentication.md). 

Im Abschnitt [Aufrufaktivitäten](#invoke-activities) wurden Sie darüber informiert, dass Anforderungen entweder eine Fortsetzungs- oder eine `tab/fetch` **Authentifizierungsantwort haben** können.  Wenn eine `tab/fetch` Anforderung ausgelöst wird und eine Antwort der **Registerkartenauthentisierung** empfängt, wird dem Benutzer die Anmeldeseite angezeigt. 

**So rufen Sie einen Authentifizierungscode über `tab/fetch` das Aufrufen ab**

1. Öffnen Sie Ihre App. Die Anmeldeseite wird angezeigt.

    > [!NOTE]
    > Das App-Logo wird über die im App-Manifest definierte Eigenschaft bereitgestellt, und der Titel wird angezeigt, nachdem das Logo in der Eigenschaft definiert wurde, die im Antworttext der Registerkarte `icon` `title` **authentifizierung** zurückgegeben wird.

1. Wählen Sie **Anmelden** aus. Sie werden zu der Authentifizierungs-URL umgeleitet, die in der `value` Eigenschaft des **Authentifizierungsantworttexts** angegeben ist. 
1. Ein Popupfenster wird geöffnet. In diesem Popupfenster wird Ihre Webseite mithilfe der Authentifizierungs-URL hostet.
1. Schließen Sie nach der Anmeldung das Fenster. Ein *Authentifizierungscode* wird an den Teams gesendet.
1. Der Teams-Client gibt die Anforderung dann erneut an Ihren Dienst weiter, der den von Ihrer gehosteten Webseite bereitgestellten Authentifizierungscode `tab/fetch` enthält. 

### <a name="tabfetch-authentication-data-flow"></a>`tab/fetch` Authentifizierungsdatenfluss

Die folgende Abbildung bietet eine Übersicht über die Funktionsweise des Authentifizierungsdatenflusses für einen `tab/fetch` Aufruf.

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Beispiel für den Authentifizierungsfluss für adaptive Kartenregisterkarten." border="false":::

**`tab/fetch` Antwort auf Authentifizierung**

Der folgende Codeausschnitt ist ein Beispiel für `tab/fetch` die Authentifizierungsantwort:

```json
// tab/auth POST response (openURL)
{
    "tab": {
        "type": "auth",
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

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein neu ausgestelltes Anforderungsbeispiel:

```json
{
    "name": "tab/fetch",
    "type": "invoke",
    "timestamp": "2021-01-15T00:10:12.253Z",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "{id}",
        "name": "John Smith",
        "aadObjectId": "00000000-0000-0000-0000-000000000000"
    },
    "conversation": {
        "tenantId": "{tenantId}",
        "id": "tab:{guid}"
    },
    "recipients": {
        "id": "28:00000000-0000-0000-0000-000000000000",
        "name": "ContosoApp"
    },
    "entities": [
        {
            "locale": "en-us",
            "country": "US",
            "platform": "Windows",
            "timezone": "America/Los_Angeles",
            "type": "clientInfo"
        }
    ],
    "channelData": {
        "tenant": { "id": "00000000-0000-0000-0000-000000000000" },
        "source": { "name": "message" }
    },
    "value": {
        "tabContext": { "tabEntityId": "homeTab" },
        "state": "0.43195668034524815"
    },
    "locale": "en-US",
    "localTimeZone": "America/Los_Angeles"
}
```

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Adaptive Karte](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)

