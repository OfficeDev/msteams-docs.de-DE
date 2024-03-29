---
title: Aufgabenmodul erstellen und versenden
author: surbhigupta
description: Erfahren Sie, wie Sie Aufgabenmodule erstellen und senden. Behandeln Sie die anfängliche Aufrufaktion, und antworten Sie mit einem Aufgabenmodul aus einem Aktionsmeldungserweiterungsbefehl.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 08629f59979923a397c08809fc20b50c81a30c58
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820115"
---
# <a name="create-and-send-task-module"></a>Aufgabenmodul erstellen und versenden

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Sie können das Aufgabenmodul mittels einer adaptiven Karte oder einer eingebetteten Webansicht erstellen. Um ein Aufgabenmodul zu erstellen, müssen Sie den Prozess ausführen, der als anfängliche Aufrufanforderung bezeichnet wird. In diesem Dokument werden die anfängliche Aufrufanforderung, Nutzlastaktivitätseigenschaften beim Aufrufen eines Aufgabenmoduls aus einem 1:1-Chat, Gruppenchat, Kanal (neuer Beitrag), Kanal (Antwort auf Thread) und Befehlsfeld behandelt.
> [!NOTE]
> Wenn das Aufgabenmodul nicht mit im App-Manifest definierten Parametern befüllt wird, müssen Sie es für Benutzer mit einer adaptiven Karte oder einer eingebetteten Webansicht erstellen.

## <a name="the-initial-invoke-request"></a>Die anfängliche Aufrufanforderung

In the process of the initial invoke request, your service receives an `Activity` object of type `composeExtension/fetchTask`, and you must respond with a `task` object containing either an Adaptive Card or a URL to the embedded web view. Along with the standard bot activity properties, the initial invoke payload contains the following request metadata:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Muss `invoke` sein. |
|`name`| Art des Befehls, der für Ihren Dienst ausgegeben wird. Muss `composeExtension/fetchTask` sein. |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Muss `compose` sein. |
|`value.context.theme` | Das Clientdesign des Benutzers; nützlich für die Formatierung eingebetteter Webansichten. Muss `default`, `contrast` oder `dark` sein. |

### <a name="example"></a>Beispiel

Der Code für die anfängliche Aufrufanforderung ist im folgenden Beispiel angegeben:

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-11-chat"></a>Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem 1:1-Chat aufgerufen wird

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem 1:1-Chat aufgerufen wird, werden wie folgt aufgelistet:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Muss `invoke` sein. |
|`name`| Art des Befehls, der für Ihren Dienst ausgegeben wird. Muss `composeExtension/fetchTask` sein. |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.source.name`| Der Name der Quelle, aus der das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Muss `compose` sein. |
|`value.context.theme` | Das Clientdesign des Benutzers; nützlich für die Formatierung eingebetteter Webansichten. Muss `default`, `contrast` oder `dark` sein. |

### <a name="example"></a>Beispiel

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem 1:1-Chat aufgerufen wird, sind im folgenden Beispiel angegeben:

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-group-chat"></a>Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Gruppenchat aufgerufen wird

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Gruppenchat aufgerufen wird, werden wie folgt aufgelistet:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Muss `invoke` sein. |
|`name`| Art des Befehls, der für Ihren Dienst ausgegeben wird. Muss `composeExtension/fetchTask` sein. |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.source.name`| Der Name der Quelle, aus der das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Muss `compose` sein. |
|`value.context.theme` | Das Clientdesign des Benutzers; nützlich für die Formatierung eingebetteter Webansichten. Muss `default`, `contrast` oder `dark` sein. |

### <a name="example"></a>Beispiel

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Gruppenchat aufgerufen wird, sind im folgenden Beispiel angegeben:

```json
{
  "type": "invoke",
  "id": "f:bf72031f-a17e-f99c-48dc-5c0714950d87",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "groupChat",
    "id": "19:d77be72390a1416e9644261e9064fa00@thread.skype",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "213167a1e3b6428b93e186ea5407c759",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-meeting-chat"></a>Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Besprechungschat aufgerufen wird

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Besprechungschat aufgerufen wird, sind im folgenden Beispiel angegeben:

```json
{
   "type": "invoke",
   "id": "f:4d271f11-4eed-622f-e820-6d82bf91692f",
   "channelId": "msteams",
   "from": {
      "id": "29:1yLsdbTM1UjxqqD8cjduNUCI1jm8xZaH3lx9u5JQ04t2bknuTCkP45TXdfROTOWk1LzN1AqTgFZUEqHIVGn_qUA",
      "name": "MOD Administrator",
      "aadObjectId": "ef16aa89-5b26-4a2c-aebb-761b551577c0"
   },
   "conversation": {
      "tenantId": "c9f9aafd-64ac-4f38-8e05-12feba3fb090",
      "id": "19:meeting_NTk4ZDY4ZmYtOWEzZS00OTRkLThhY2EtZmUzZmUzMDQyM2M0@thread.v2",
      "name": "Test meeting"
   },   
   "channelData": {
      "tenant": {
         "id": "c9f9aafd-64ac-4f38-8e05-12feba3fb090"
      },
      "source": {
         "name": "compose"
      },
      "meeting": {
         "id": "MCMxOTptZWV0aW5nX05UazRaRFk0Wm1ZdE9XRXpaUzAwT1RSa0xUaGhZMkV0Wm1VelptVXpNRFF5TTJNMEB0aHJlYWQudjIjMA=="
      }
   },
   "value": {
      "commandId": "Test",
      "commandContext": "compose",
      "requestId": "c46a6b53573f42b5bc801716e5ccc960",
      "context": {
         "theme": "default"
      }
   },
   "name": "composeExtension/fetchTask",
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-new-post"></a>Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (neuer Beitrag)

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (neuer Beitrag), werden wie folgt aufgelistet:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Muss `invoke` sein. |
|`name`| Art des Befehls, der für Ihren Dienst ausgegeben wird. Muss `composeExtension/fetchTask` sein. |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.source.name`| Der Name der Quelle, aus der das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Muss `compose` sein. |
|`value.context.theme` | Das Clientdesign des Benutzers; nützlich für die Formatierung eingebetteter Webansichten. Muss `default`, `contrast` oder `dark` sein. |

### <a name="example"></a>Beispiel

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Kanal aufgerufen wird (neuer Beitrag), sind im folgenden Beispiel angegeben:

```json
{
  "type": "invoke",
  "id": "f:a5fbb109-c989-c449-ee83-71ac99919d4b",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "5336640edc7748b28ce2df43f5b45963",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-reply-to-thread"></a>Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (Antwort auf Thread)

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul über einen Kanal aufgerufen wird (Antwort auf Thread), werden wie folgt aufgelistet:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Muss `invoke` sein. |
|`name`| Art des Befehls, der für Ihren Dienst ausgegeben wird. Muss `composeExtension/fetchTask` sein. |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.channel.id`| Kanal-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.team.id`| Team-ID (wenn die Anforderung in einem Kanal erfolgt ist). |
|`channelData.source.name`| Der Name der Quelle, aus der das Aufgabenmodul aufgerufen wird. |
|`ChannelData.legacy. replyToId`| Ruft die ID der Nachricht ab, auf die diese Nachricht eine Antwort ist, oder legt sie fest. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Muss `compose` sein. |
|`value.context.theme` | Das Clientdesign des Benutzers; nützlich für die Formatierung eingebetteter Webansichten. Muss `default`, `contrast` oder `dark` sein. |

### <a name="example"></a>Beispiel

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Kanal aufgerufen wird (Antwort auf Thread), sind im folgenden Beispiel angegeben:

```json
{
  "type": "invoke",
  "id": "f:19ccc884-c792-35ef-2f40-d0ff43dcca71",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype;messageid=1611060744833",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "message",
    "requestId": "7f7d22efe5414818becebcec649a7912",
    "messagePayload": {
      "linkToMessage": "https://teams.microsoft.com/l/message/19:6decf54d86d945e4b3924b63a9161a78@thread.skype/1611060744833",
      "id": "1611060744833",
      "replyToId": null,
      "createdDateTime": "2021-01-19T12:52:24.833Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "<div><div><at id=\"0\">Testing outgoing Webhook-Nikitha</at> - Hi</div>\n</div>"
      },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc",
          "displayName": "Olo Brockhouse"
        },
        "application": null
      },
      "reactions": [],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Testing outgoing Webhook-Nikitha",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": null,
            "application": {
              "applicationIdentityType": "webhook",
              "id": "b8c1c68c-e290-4bdd-81c3-266f310751dc",
              "displayName": "Testing outgoing Webhook-Nikitha"
            }
          }
        }
      ],
      "attachments": []
    },
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-command-box"></a>Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul aus einem Befehlsfeld aufgerufen wird

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird, werden wie folgt aufgelistet:

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Anforderungstyp. Muss `invoke` sein. |
|`name`| Art des Befehls, der für Ihren Dienst ausgegeben wird. Muss `composeExtension/fetchTask` sein. |
|`from.id`| ID des Benutzers, der die Anforderung gesendet hat. |
|`from.name`| Name des Benutzers, der die Anforderung gesendet hat. |
|`from.aadObjectId`| Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
|`channelData.tenant.id`| Azure Active Directory Mandanten-ID. |
|`channelData.source.name`| Der Name der Quelle, aus der das Aufgabenmodul aufgerufen wird. |
|`value.commandId` | Enthält die ID des Befehls, der aufgerufen wurde. |
|`value.commandContext` | Der Kontext, der das Ereignis ausgelöst hat. Muss `compose` sein. |
|`value.context.theme` | Das Clientdesign des Benutzers; nützlich für die Formatierung eingebetteter Webansichten. Muss `default`, `contrast` oder `dark` sein. |

### <a name="example"></a>Beispiel

Die Eigenschaften von Nutzlastaktivitäten, wenn ein Aufgabenmodul über ein Befehlsfeld aufgerufen wird, sind im folgenden Beispiel angegeben:

```json
{
  "type": "invoke",
  "id": "f:172560f1-95f9-3189-edb2-b7612cd1a3cd",
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "compose",
    "requestId": "d2ce690cdc2b4920a538e75882610a30",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

### <a name="example"></a>Beispiel

Der folgende Codeabschnitt ist ein Beispiel für eine `fetchTask`-Anforderung:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "name": "composeExtension/fetchTask",
  "type": "invoke",
  "timestamp": "2019-07-01T22:57:22.175Z",
  "localTimestamp": "2019-07-01T15:57:22.175-07:00",
  "id": "f:0123456878990178955",
  "channelId": "msteams",
  "serviceURL": "https://smba.trafficmanager.net/amer/",
  "from": {
    "id": "29:1test2GgHIa0DXzDT_OGwL5vSMZdAxDlGR7hYxZ6_JBVqHz2Zq9Nm44FUNWqHCdGBwHg8WrlFRsYrd0cCAS7dig",
    "name": "John Smith",
    "aadObjectId": "1234567d-1234-462a-8952-35b75f16f1e1"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "tenantId": "1234abcd-1234-12ab-12ab-35b75f16f1e1",
    "id": "19:83ed1d507cb5427c93495cf914326310@thread.skype"
  },
  "recipient": {
    "id": "28:049566e0-4401-4bcf-86a1-ce22082ce03a",
    "name": "mess"
  },
  "entities": [
    {
      "locale": "en-US",
      "country": "US",
      "platform": "Windows",
      "type": "clientInfo"
    }
  ],
  "channelData": {
    "channel": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "team": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "tenant": {
      "id": "1234abcd-1234-12ab-12ab-35b75f16f1e1"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "hello",
    "commandContext": "compose",
    "context": {
      "theme": "dark"
    }
  },
  "locale": "en-US"
}
```

* * *

## <a name="initial-invoke-request-from-a-message"></a>Anfängliche Aufrufanforderung aus einer Nachricht

Wenn Ihr Bot aus einer Nachricht aufgerufen wird, muss das `value`-Objekt in der anfänglichen Aufrufanforderung die Details der Nachricht enthalten, aus der Ihre Nachrichtenerweiterung aufgerufen wird. Die Arrays `reactions` und `mentions` sind optional und nicht vorhanden, wenn die ursprüngliche Nachricht keine Reaktionen oder Erwähnungen enthält.
Der folgende Abschnitt ist ein Beispiel für das `value`-Objekt:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
...
  "value": {
    "commandId": "setReminder",
    "commandContext": "message",
    "messagePayload": {
      "id": "1111111111",
      "replyToId": null,
      "createdDateTime": "2019-02-25T21:29:36.065Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "subject": "Message subject",
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "This is the message the messaging extension was invoked from."
    },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "wxyz12ab8-ab12-cd34-ef56-098abc123876",
          "displayName": "Jamie Smythe"
        },
        "application": null
      },
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2019-02-25T22:40:40.806Z",
          "user": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "qrst12346-ab12-cd34-ef56-098abc123876",
              "displayName": "Jim Brown"
            },
            "application": null
          }
        }
      ],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Sarah",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "ab12345678-ab12-cd34-ef56-098abc123876",
              "displayName": "Sarah"
            },
            "application": null
          }
        }
      ]
    }
  ...
```

* * *

## <a name="respond-to-the-fetchtask"></a>Reagieren auf fetchTask

Antworten Sie auf die Aufrufanforderung mit einem `task`-Objekt, das ein `taskInfo`-Objekt mit der adaptiven Karte oder einer Web-URL oder eine einfache Zeichenfolgennachricht enthält.

|Eigenschaftenname|Zweck|
|---|---|
|`type`| Kann entweder `continue` zum Präsentieren eines Formulars oder `message` für ein einfaches Popupfenster verwendet werden. |
|`value`| Entweder ein `taskInfo`-Objekt für ein Formular oder ein `string`-Objekt für eine Nachricht. |

Das Schema für das taskInfo-Objekt ist wie folgt:

|Eigenschaftenname|Zweck|
|---|---|
|`title`| Der Titel des Aufgabenmoduls.|
|`height`| Muss entweder eine ganze Zahl (in Pixel) sein oder `small`, `medium` oder `large` lauten.|
|`width`| Muss entweder eine ganze Zahl (in Pixel) sein oder `small`, `medium` oder `large` lauten.|
|`card`| Die adaptive Karte, die das Formular definiert (sofern verwendet).
|`url`| Die URL, die innerhalb des Aufgabenmoduls als eingebettete Webansicht geöffnet werden soll.|
|`fallbackUrl`| Wenn ein Client das Feature "Aufgabenmodul" nicht unterstützt, wird diese URL in einem Browser-Tab geöffnet. |

### <a name="respond-to-the-fetchtask-with-an-adaptive-card"></a>Reagieren auf fetchTask mit einer adaptiven Karte

Wenn Sie eine adaptive Karte verwenden, müssen Sie mit einem `task`-Objekt mit dem `value`-Objekt antworten, das eine adaptive Karte enthält.

#### <a name="example"></a>Beispiel

Der folgende Codeabschnitt ist ein Beispiel für die Antwort an `fetchTask` mit einer adaptiven Karte:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

In diesem Beispiel wird zusätzlich zum Bot Framework SDK das [AdaptiveCards NuGet-Paket](https://www.nuget.org/packages/AdaptiveCards) verwendet.

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Card = new Attachment()
        {
          ContentType = AdaptiveCard.ContentType,
          Content = new AdaptiveCard("1.0")
          {
            Body = new List<AdaptiveElement>()
            {
              new AdaptiveTextInput() { Id = "FormField1", Placeholder = placeholder},
              new AdaptiveTextInput() { Id = "FormField2", Placeholder = "FormField2"},
              new AdaptiveTextInput() { Id = "FormField3", Placeholder = "FormField3"},
            },
            Actions = new List<AdaptiveAction>()
            {
              new AdaptiveSubmitAction()
              {
                Type = AdaptiveSubmitAction.TypeName,
                Title = "Submit",
              },
            },
          },
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    handleTeamsMessagingExtensionFetchTask(context, action) {
      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [{
          data: { submitLocation: 'messagingExtensionFetchTask'},
          title: 'Submit',
          type: 'Action.Submit'
        }],
        body: [
          { text: 'Task Module', type: 'TextBlock', weight: 'bolder'},
          { type: 'TextBlock', text: 'Enter text for Question:' },
          { id: 'Question', placeholder: 'Question text here', type: 'Input.Text', value: userText },
          { type: 'TextBlock', text: 'Options for Question:' },
          { type: 'TextBlock', text: 'Is Multi-Select:' },
          {
            choices: [{ title: 'True', value: 'true' }, { title: 'False', value: 'false' }],
            id: 'MultiSelect',
            isMultiSelect: false,
            style: 'expanded',
            type: 'Input.ChoiceSet',
            value: isMultiSelect ? 'true' : 'false'
          },
          { id: 'Option1', placeholder: 'Option 1 here', type: 'Input.Text', value: option1 },
          { id: 'Option2', placeholder: 'Option 2 here', type: 'Input.Text', value: option2 }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });

      return {
        task: {
          type: 'continue',
          value: {
            card: adaptiveCard,
            height: 450,
            title: 'Task Module Fetch Example',
            url: null,
            width: 500
          }
        }
      };
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
 {
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "card": {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Input.Text",
            "placeholder": "FormField1",
            "id": "FormField1"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField2",
            "id": "FormField2"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField3",
            "id": "FormField3"
          },
          {
            "type": "ActionSet",
            "actions": [
              {
                "type": "Action.Submit",
                "title": "Action.Submit",
                "id": "submitAction"
              }
            ]
          }
        ]
      }
    }
  }
}
```

* * *

### <a name="create-a-task-module-with-an-embedded-web-view"></a>Erstellen eines Aufgabenmoduls mit einer eingebetteten Webansicht

Wenn Sie eine eingebettete Webansicht verwenden, müssen Sie mit einem `task`-Objekt mit dem `value`-Objekt antworten, das die URL zu dem Webformular enthält, das geladen werden soll. Die Domänen aller URLs, die geladen werden sollen, müssen im `validDomains`-Array im Manifest Ihrer App enthalten sein. Weitere Informationen zum Erstellen einer eingebetteten Webansicht finden Sie in der [Dokumentation zu Aufgabenmodulen](~/task-modules-and-cards/what-are-task-modules.md).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Url = "https://contoso.com/msteams/taskmodules/newcustomer",
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    return {
      task: {
        type: 'continue',
        value: {
          width: 500,
          height: 450,
          title: 'Task Module Fetch Example',
          url: 'https://contoso.com/msteams/taskmodules/newcustomer',
          fallbackUrl: 'https://contoso.com/msteams/taskmodules/newcustomer'
        }
      }
    };
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "url": "https://contoso.com/msteams/taskmodules/newcustomer",
      "fallbackUrl": "https://contoso.com/msteams/taskmodules/newcustomer"
    }
  }
}
```

* * *

### <a name="request-to-install-your-conversational-bot"></a>Anfordern der Installation Ihres Unterhaltungs-Bots

Wenn die App einen Unterhaltungs-Bot enthält, installieren Sie den Bot in der Unterhaltung, und laden Sie dann das Aufgabenmodul. Der Bot ist nützlich, um zusätzlichen Kontext für das Aufgabenmodul abzurufen. Ein Beispiel für dieses Szenario ist das Abrufen einer Liste zum Befüllen eines Personenauswahl-Steuerelements oder der Liste der Kanäle in einem Team.

Wenn die Nachrichtenerweiterung den `composeExtension/fetchTask`-Aufruf empfängt, überprüfen Sie, ob der Bot im aktuellen Kontext installiert ist, um den Fluss zu erleichtern. Überprüfen Sie z. B. den Fluss durch das Abrufen einer Liste. Wenn der Bot nicht installiert ist, geben Sie eine adaptive Karte mit einer Aktion zurück, die den Benutzer auffordert, den Bot zu installieren. Der Benutzer muss über die Berechtigung zum Installieren der Apps an diesem Speicherort für die Überprüfung verfügen. Wenn die App-Installation fehlschlägt, erhält der Benutzer eine Nachricht, in der er aufgefordert wird, sich an den Administrator zu wenden.

#### <a name="example"></a>Beispiel

Der folgende Codeabschnitt ist ein Beispiel für die Antwort:

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Looks like you haven't used Disco in this team/chat"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Continue",
      "data": {
        "msteams": {
          "justInTimeInstall": true
        }
      }
    }
  ],
  "version": "1.0"
}
```

Nach der Installation des Unterhaltungs-Bots folgt eine weitere Aufrufnachricht mit `name = composeExtension/submitAction` und `value.data.msteams.justInTimeInstall = true`.

#### <a name="example"></a>Beispiel

Der folgende Codeabschnitt ist ein Beispiel für die Aufgabenantwort auf den Aufruf:

```json
{
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "msteams": {
        "justInTimeInstall": true
      }
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  },
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith"
}
```

Die Aufgabenantwort auf den Aufruf muss der des installierten Bots ähneln.

#### <a name="example"></a>Beispiel

Der folgende Codeabschnitt ist ein Beispiel für die Just-in-Time-Installation der App mit adaptiver Karte:

```csharp
private static Attachment GetAdaptiveCardAttachmentFromFile(string fileName)
  {
      //Read the card json and create attachment.
         string[] paths = { ".", "Resources", fileName };
         var adaptiveCardJson = File.ReadAllText(Path.Combine(paths));
         var adaptiveCardAttachment = new Attachment()
            {
                ContentType = "application/vnd.microsoft.card.adaptive",
                Content = JsonConvert.DeserializeObject(adaptiveCardJson),
            };
            return adaptiveCardAttachment;
        }
```

* * *

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   | Python |
|:---------------------|:--------------|:---------|:--------|
|Teams-Nachrichtenerweiterungen – Aktion| Beschreibt, wie Aktionsbefehle definiert werden, ein Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktionen reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
|Teams Nachrichtenerweiterungen – Suche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Antworten auf Aktionsbefehle](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

## <a name="see-also"></a>Siehe auch

* [Karten](../../../task-modules-and-cards/what-are-cards.md)
* [Personenauswahl in Adaptiven Karten](../../../task-modules-and-cards/cards/people-picker.md)
* [Aufgabenmodule](../../../task-modules-and-cards/what-are-task-modules.md)
* [App-Manifestschema für Teams](../../../resources/schema/manifest-schema.md)
* [Definieren von Aktionsbefehlen für Nachrichtenerweiterungen](define-action-command.md)
* [Nachrichtenerweiterungen](../../what-are-messaging-extensions.md)
