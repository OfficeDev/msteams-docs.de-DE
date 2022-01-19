---
title: Erstellen adaptiver Kartenregisterkarten
author: KirtiPereira
description: Erfahren Sie mehr über das Erstellen von Registerkarten mit adaptiven Karten mit Codebeispielen, einschließlich des Aufrufens von Aktivitäten, des Verständnisses des Aufgabenmodulworkflows und der Authentifizierung.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: none
keywords: Datenfluss der Authentifizierungsdaten für persönliche Apps für adaptive Karten
ms.openlocfilehash: f2b6c78293a2bc6f25e3989f6eba4c4e2833aaee
ms.sourcegitcommit: c65a868744e4108b5d786de2350981e3f1f05718
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2022
ms.locfileid: "62080967"
---
# <a name="build-tabs-with-adaptive-cards"></a>Erstellen von Registerkarten mit adaptiven Karten

> [!IMPORTANT]
> * Registerkarten mit adaptiven Karten werden derzeit nur als persönliche Apps unterstützt.

Beim Entwickeln einer Registerkarte mithilfe der herkömmlichen Methode können folgende Probleme auftreten:

* Überlegungen zu HTML und CSS
* Langsame Ladezeiten
* iFrame-Einschränkungen
* Serverwartung und Kosten

Registerkarten für adaptive Karten sind eine neue Möglichkeit zum Erstellen von Registerkarten in Teams. Anstatt Webinhalte in einen IFrame einzubetten, können Sie adaptive Karten auf einer Registerkarte rendern. Während das Front-End mit adaptiven Karten gerendert wird, wird das Back-End von einem Bot unterstützt. Der Bot ist dafür verantwortlich, Anforderungen zu akzeptieren und entsprechend mit der gerenderten adaptiven Karte zu antworten.

Sie können Ihre Registerkarten mit vorgefertigten Bausteinen für die Benutzeroberfläche (UI) erstellen, die auf Desktops, im Web und auf mobilgeräten systemeigen sind. Dieser Artikel hilft Ihnen zu verstehen, welche Änderungen am App-Manifest vorgenommen werden müssen. In diesem Artikel wird auch beschrieben, wie die Aufrufaktivität Informationen auf der Registerkarte mit adaptiven Karten anfordert und sendet und welche Auswirkungen dies auf den Aufgabenmodulworkflow hat.

Die folgende Abbildung zeigt Buildregisterkarten mit adaptiven Karten auf Desktops und mobilgeräten:

:::image type="content" source="../../assets/images/tabs/adaptive-cards-rendered-in-tabs.jpg" alt-text="Beispiel für eine adaptive Karte, die auf Registerkarten gerendert wird." border="false":::

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit der Verwendung adaptiver Karten zum Erstellen von Registerkarten beginnen, müssen Sie Folgendes tun:

* Machen Sie sich mit [der Bot-Entwicklung,](../../bots/what-are-bots.md) [adaptiven Karten](https://adaptivecards.io/)und [Aufgabenmodulen](../../task-modules-and-cards/task-modules/task-modules-bots.md) in Teams vertraut.
* Lassen Sie einen Bot in Teams für Ihre Entwicklung ausführen.

## <a name="changes-to-app-manifest"></a>Änderungen am App-Manifest

Persönliche Apps, die Registerkarten rendern, müssen ein `staticTabs` Array in ihrem App-Manifest enthalten. Registerkarten für adaptive Karten werden gerendert, wenn die `contentBotId` Eigenschaft in der Definition bereitgestellt `staticTab` wird. Statische Registerkartendefinitionen müssen entweder eine , eine Registerkarte für `contentBotId` adaptive Karten oder eine , die eine typische `contentUrl` gehostete Webinhaltsregisterkarte angeben.

> [!NOTE]
> Die `contentBotId` Eigenschaft ist derzeit in der Manifestversion 1.9 oder höher verfügbar.

Stellen Sie der `contentBotId` Eigenschaft die Eigenschaft `botId` bereit, mit der die Registerkarte "Adaptive Karte" kommunizieren muss. Die `entityId` für die Registerkarte "Adaptive Karte" konfigurierte Karte wird im Parameter jeder Aufrufanforderung gesendet und kann verwendet `tabContext` werden, um adaptive Kartenregisterkarten zu unterscheiden, die vom gleichen Bot unterstützt werden. Weitere Informationen zu anderen statischen Registerkartendefinitionsfeldern finden Sie unter [Manifestschema.](../../resources/schema/manifest-schema.md#statictabs)

Es folgt ein Beispiel für ein Registerkartenmanifest für adaptive Karten:

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

Die Kommunikation zwischen Ihrer Registerkarte "Adaptive Karte" und Ihrem Bot erfolgt über `invoke` Aktivitäten. Jede `invoke` Aktivität hat einen entsprechenden **Namen.** Verwenden Sie den Namen jeder Aktivität, um jede Anforderung zu unterscheiden. `tab/fetch` und `tab/submit` sind die in diesem Abschnitt behandelten Aktivitäten.

> [!NOTE]
> * Bots müssen alle Antworten an die [Dienst-URL](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#base-uri&preserve-view=true)senden. Die Dienst-URL wird als Teil der eingehenden `activity` Nutzlast empfangen.
> * Die Nutzlastgröße des Aufrufs wurde auf 80 KB erhöht.

### <a name="fetch-adaptive-card-to-render-to-a-tab"></a>Abrufen einer adaptiven Karte zum Rendern auf einer Registerkarte

`tab/fetch`ist die erste Aufrufanforderung, die Ihr Bot empfängt, wenn ein Benutzer eine Registerkarte für adaptive Karten öffnet. Wenn Ihr Bot die Anforderung empfängt, sendet er entweder eine **Antwort** zur Fortsetzung der Registerkarte oder eine **Tab-Authentifizierungsantwort.**
Die **Fortsetzungsantwort** enthält ein Array für **Karten,** das vertikal auf der Registerkarte in der Reihenfolge des Arrays gerendert wird.

> [!NOTE]
> Weitere Informationen zur **Authentifizierungsantwort** finden Sie unter ["Authentifizierung".](#authentication)

Der folgende Code enthält Beispiele für `tab/fetch` Anforderung und Antwort:

**`tab/fetch` Anfrage**

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

**`tab/fetch` Antwort**

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
                },
                {
                    "card": adaptiveCard3
                }  
            ]
        },
    },
    "responseType": "tab"
}
```

### <a name="handle-submits-from-adaptive-card"></a>Verarbeiten von Übermittlungen von einer adaptiven Karte

Nachdem eine adaptive Karte auf der Registerkarte gerendert wurde, kann sie auf Benutzerinteraktionen reagieren. Diese Antwort wird von der `tab/submit` Aufrufanforderung verarbeitet.

Wenn ein Benutzer eine Schaltfläche auf der Registerkarte "Adaptive Karte" auswählt, wird die `tab/submit` Anforderung an Ihren Bot mit den entsprechenden Daten über die Funktion der `Action.Submit` adaptiven Karte ausgelöst. Die Daten der adaptiven Karte sind über die Dateneigenschaft der `tab/submit` Anforderung verfügbar. Sie erhalten eine der folgenden Antworten auf Ihre Anforderung:

* Eine HTTP-Statuscodeantwort `200` ohne Textkörper. Eine leere 200-Antwort führt dazu, dass der Client keine Aktion ausführt.
* Auf der `200` Standardregisterkarte wird die Antwort **fortgesetzt,** wie beim [Abrufen einer adaptiven Karte](#fetch-adaptive-card-to-render-to-a-tab)erläutert. Eine **Fortsetzungsantwort** der Registerkarte löst aus, dass der Client die gerenderte Registerkarte "Adaptive Karte" mit den adaptiven Karten aktualisiert, die im Kartenarray der **Fortsetzungsantwort** bereitgestellt werden.

Der folgende Code enthält Beispiele für `tab/submit` Anforderung und Antwort:

**`tab/submit` Anfrage**

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

**`tab/submit` Antwort**

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

## <a name="understand-task-module-workflow"></a>Grundlegendes zum Aufgabenmodulworkflow

Das Aufgabenmodul verwendet auch adaptive Karte zum Aufrufen `task/fetch` und `task/submit` Anfordern und Antworten. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Microsoft Teams Bots.](../../task-modules-and-cards/task-modules/task-modules-bots.md)

Mit der Einführung der Registerkarte "Adaptive Karte" gibt es eine Änderung in der Art und Weise, wie der Bot auf eine `task/submit` Anforderung antwortet. Wenn Sie eine Registerkarte für adaptive Karten verwenden, antwortet der Bot auf die `task/submit` Aufrufanforderung mit der Standardregisterkarte **"Continue"-Antwort** und schließt das Aufgabenmodul. Die Registerkarte "Adaptive Karte" wird aktualisiert, indem die neue Liste der Karten gerendert wird, die im Antworttext der Registerkarte **"Fortsetzen"** bereitgestellt wird.

### <a name="invoke-taskfetch"></a>Aufrufen `task/fetch`

Der folgende Code enthält Beispiele für `task/fetch` Anforderung und Antwort:

**`task/fetch` Anfrage**
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

**`task/fetch` Antwort**

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

### <a name="invoke-tasksubmit"></a>Aufrufen `task/submit`

Der folgende Code enthält Beispiele für `task/submit` Anforderung und Antwort:

**`task/submit` Anfrage**

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

**`task/submit` Registerkartenantworttyp**

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

In den vorherigen Abschnitten haben Sie gesehen, dass die meisten Entwicklungsparadigmen aus den Aufgabenmodulanforderungen und -antworten in Registerkartenanforderungen und -antworten erweitert werden können. Wenn es um die Behandlung der Authentifizierung geht, folgt der Workflow für die Registerkarte "Adaptive Karte" dem Authentifizierungsmuster für Messaging-Erweiterungen. Weitere Informationen finden Sie unter Hinzufügen der [Authentifizierung.](../../messaging-extensions/how-to/add-authentication.md)

`tab/fetch` Anforderungen können entweder eine **Fortsetzungs-** oder eine **Authentifizierungsantwort** haben. Wenn eine `tab/fetch` Anforderung ausgelöst wird und eine Registerkartenauthentifizierungsantwort empfängt, wird dem Benutzer die Anmeldeseite angezeigt. 

**So rufen Sie einen Authentifizierungscode durch Aufrufen ab `tab/fetch`**

1. Öffnen Sie Ihre App. Die Anmeldeseite wird angezeigt.

    > [!NOTE]
    > Das App-Logo wird über die `icon` im App-Manifest definierte Eigenschaft bereitgestellt. Der Titel, der angezeigt wird, nachdem das Logo in der Eigenschaft definiert wurde, `title` die im Antworttext der **Registerkartenauthentifizierung** zurückgegeben wird.

1. Wählen Sie **Anmelden** aus. Sie werden zu der Authentifizierungs-URL umgeleitet, die in der `value` Eigenschaft des **Authentifizierungsantworttexts** angegeben ist.
1. Ein Popupfenster wird geöffnet. In diesem Popupfenster wird Ihre Webseite mithilfe der Authentifizierungs-URL gehostet.
1. Schließen Sie nach der Anmeldung das Fenster. Ein **Authentifizierungscode** wird an den Teams Client gesendet.
1. Der Teams-Client sendet dann die `tab/fetch` Anforderung erneut an Ihren Dienst, der den von Ihrer gehosteten Webseite bereitgestellten Authentifizierungscode enthält.

### <a name="tabfetch-authentication-data-flow"></a>`tab/fetch` Authentifizierungsdatenfluss

Die folgende Abbildung enthält eine Übersicht über die Funktionsweise des Authentifizierungsdatenflusses für einen `tab/fetch` Aufruf.

:::image type="content" source="../../assets/images/tabs/adaptive-cards-tab-auth-flow.png" alt-text="Beispiel für den Authentifizierungsfluss für adaptive Kartenregisterkarten." border="false":::

**`tab/fetch` Authentifizierungsantwort**

Der folgende Code enthält ein Beispiel für die `tab/fetch` Authentifizierungsantwort:

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

Der folgende Code zeigt ein neu ausgestelltes Anforderungsbeispiel:

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

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** |**.NET** | **Node.js** |
|----------------|-----------------|--------------|--------------|
| Adaptive Karten auf Teams Registerkarte anzeigen | Microsoft Teams Beispielcode der Registerkarte, der veranschaulicht, wie adaptive Karten in Teams angezeigt werden. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-adaptive-cards/csharp)| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-adaptive-cards/nodejs) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Registerkarten-Link - Verbreitung und Phasenansicht](~/tabs/tabs-link-unfurling.md)

## <a name="see-also"></a>Siehe auch

* [Adaptive Karte](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Feedback zum Ausfüllen des Formulars](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)