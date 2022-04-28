---
title: Bot-Aktivitätenhandler
author: surbhigupta
description: Grundlegendes zu den Bot-Aktivitätshandlern in Teams.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
keywords: Aktivitätshandler-Framework Bot-Karten-Zustimmungskanalereignis
ms.openlocfilehash: 34dd5e8042b71f4e7cc78df7e7c543c86a53f58e
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104035"
---
# <a name="bot-activity-handlers"></a>Bot-Aktivitätenhandler

Dieses Dokument baut auf dem Artikel über die [Funktionsweise von Bots](https://aka.ms/how-bots-work) in der wichtigsten [Bot Framework-Dokumentation](https://aka.ms/azure-bot-service-docs) auf. Der Hauptunterschied zwischen Bots, die für Microsoft Teams entwickelt wurden, und dem Kern-Bot-Framework liegt in den Features, die in Teams bereitgestellt werden.

Zum Organisieren der Unterhaltungslogik für Ihren Bot wird ein Aktivitätshandler verwendet. Aktivitäten werden auf zwei Arten mit Teams Aktivitätshandlern und Botlogik behandelt. Der Teams-Aktivitätshandler fügt Unterstützung für Microsoft Teams-spezifische Ereignisse und Interaktionen hinzu. Das Botobjekt enthält die Unterhaltungslogik für einen Turn und macht einen Turn-Handler verfügbar. Dies ist die Methode, die eingehende Aktivitäten vom Botadapter akzeptieren kann.

## <a name="teams-activity-handlers"></a>Teams Aktivitätshandler

Teams Aktivitätshandler wird vom Aktivitätshandler Microsoft Bot Framework abgeleitet. Es leitet alle Teams Aktivitäten weiter, bevor nicht Teams bestimmte Aktivitäten behandelt werden können.

Wenn ein Bot für Teams eine Aktivität empfängt, wird er an die Aktivitätshandler weitergeleitet. Alle Aktivitäten werden über einen Basishandler weitergeleitet, der als Turn-Handler bezeichnet wird. Der Turn-Handler ruft den erforderlichen Aktivitätshandler auf, um alle empfangenen Aktivitäten zu verwalten. Der Teams Bot wird von der `TeamsActivityHandler` Klasse abgeleitet, die von der Klasse des Bot Frameworks `ActivityHandler` abgeleitet wird.

# <a name="c"></a>[C#](#tab/csharp)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turn-Handler sendet dann die eingehende Aktivität an den `OnMessageActivityAsync` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turn-Handler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `OnConversationUpdateActivityAsync`. Der Teams-Aktivitätshandler sucht zunächst nach Teams bestimmten Ereignissen.The Teams activity handler first checks for any Teams specific events. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot-Frameworks übergeben.

In der Teams Aktivitätshandlerklasse gibt es zwei primäre Teams Aktivitätshandler `OnConversationUpdateActivityAsync` und `OnInvokeActivityAsync`. `OnConversationUpdateActivityAsync`leitet alle Unterhaltungsaktualisierungsaktivitäten und `OnInvokeActivityAsync` leitet alle Teams Aktivitäten aufzurufen.

Um Ihre Logik für Teams bestimmten Aktivitätshandler zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt "[Botlogik](#bot-logic)" gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die gewünschte Logik in ihrer Außerkraftsetzung hinzufügen.

Die Codeausschnitte für Teams Aktivitätshandler:

`OnTeamsChannelCreatedAsync`

```csharp

protected override Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            // Code logic here
        }
```

`OnTeamsChannelDeletedAsync`

```csharp

protected override Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            // Code logic here
        }
```

`OnTeamsChannelRenamedAsync`

```csharp

protected override Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
  {
   // Code logic here
  }
```

`OnTeamsTeamRenamedAsync`

```csharp

protected override Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
  {
   // Code logic here
  }
```

`OnTeamsMembersAddedAsync`

```csharp

protected override Task OnTeamsMembersAddedAsync(IList<TeamsChannelAccount> teamsMembersAdded, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
  {
   // Code logic here
  }
```

`OnTeamsMembersRemovedAsync`

```csharp

protected override Task OnTeamsMembersRemovedAsync(IList<TeamsChannelAccount> teamsMembersRemoved, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken);
  {
   // Code logic here
  }
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turn-Handler sendet dann die eingehende Aktivität an den `onMessage` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turn-Handler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `dispatchConversationUpdateActivity`. Der Teams-Aktivitätshandler sucht zunächst nach Teams bestimmten Ereignissen.The Teams activity handler first checks for any Teams specific events. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot-Frameworks übergeben.

In der Teams Aktivitätshandlerklasse gibt es zwei primäre Teams Aktivitätshandler `dispatchConversationUpdateActivity` und `onInvokeActivity`. `dispatchConversationUpdateActivity`leitet alle Unterhaltungsaktualisierungsaktivitäten und `onInvokeActivity` leitet alle Teams Aktivitäten aufzurufen.

Um Ihre Logik für Teams bestimmten Aktivitätshandler zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt "[Botlogik](#bot-logic)" gezeigt. Definieren Sie ihre Botlogik für diese Handler, und rufen `next()` Sie dann am Ende auf. Durch Aufrufen stellen `next()` Sie sicher, dass der nächste Handler ausgeführt wird.

Die Codeausschnitte für Teams Aktivitätshandler:

`OnTeamsChannelCreatedAsync`

```javascript

onTeamsChannelCreated(async (channelInfo, teamInfo, context, next) => {
       // code for handling
        await next()
    });
```

`OnTeamsChannelDeletedAsync`

```javascript

onTeamsChannelDeleted(async (channelInfo, teamInfo, context, next) => {
       // code for handling
       await next()
    });
```

`OnTeamsChannelRenamedAsync`

```javascript

onTeamsChannelRenamed(async (channelInfo, teamInfo, context, next) => {
       // code for handling
       await next()
    });
```

`OnTeamsTeamRenamedAsync`

```javascript

onTeamsTeamRenamedAsync(async (teamInfo, context, next) => {
       // code for handling
       await next()
    });
```

`OnTeamsMembersAddedAsync`

```javascript

onTeamsMembersAdded(async (membersAdded, teamInfo, context, next) => {
       // code for handling
    await next();
    });
```

`OnTeamsMembersRemovedAsync`

```javascript

onTeamsMembersRemoved(async (membersRemoved, teamInfo, context, next) => {
       // code for handling
    await next();
    });
```

# <a name="python"></a>[Python](#tab/python)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turn-Handler sendet dann die eingehende Aktivität an den `on_message_activity` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turn-Handler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `on_conversation_update_activity`. Der Teams-Aktivitätshandler sucht zunächst nach Teams bestimmten Ereignissen.The Teams activity handler first checks for any Teams specific events. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot-Frameworks übergeben.

In der Teams Aktivitätshandlerklasse gibt es zwei primäre Teams Aktivitätshandler `on_conversation_update_activity` und `on_invoke_activity`. `on_conversation_update_activity`leitet alle Unterhaltungsaktualisierungsaktivitäten und `on_invoke_activity` leitet alle Teams Aktivitäten aufzurufen.

Um Ihre Logik für Teams bestimmten Aktivitätshandler zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt "[Botlogik](#bot-logic)" gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die gewünschte Logik in ihrer Außerkraftsetzung hinzufügen.

---

## <a name="bot-logic"></a>Botlogik

Die Botlogik verarbeitet eingehende Aktivitäten aus einem oder mehreren Bot-Kanälen und generiert als Reaktion ausgehende Aktivitäten. Dies gilt weiterhin für Bots, die von der Teams Aktivitätshandlerklasse abgeleitet wurden, die zuerst nach Teams Aktivitäten sucht. Nach der Überprüfung auf Teams Aktivitäten übergibt es alle anderen Aktivitäten an den Aktivitätshandler des Bot-Frameworks.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
>
>* Mit Ausnahme der **Aktivitäten der hinzugefügten** und **entfernten** Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem nicht Teams Bot.
>* `onInstallationUpdateActivityAsync()`wird verwendet, um Teams Gebietsschema abzurufen, während der Bot zu Teams hinzugefügt wird.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem ein neues Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten `ActivityHandler` Handler umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `OnTurnAsync` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Empfangene Nachrichtenaktivität | `OnMessageActivityAsync` | Diese Methode kann überschrieben werden, um eine `Message` Aktivität zu behandeln. |
| Unterhaltungsaktualisierungsaktivität empfangen | `OnConversationUpdateActivityAsync` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer `ConversationUpdate` Aktivität beigetreten sind oder diese verlassen haben. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `OnMembersAddedAsync` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `OnEventActivityAsync` | Diese Methode ruft einen für den Ereignistyp spezifischen Handler für eine `Event` Aktivität auf. |
| Empfangene Token-Antwort-Ereignisaktivität | `OnTokenResponseEventAsync` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Ereignisaktivität ohne Tokenantwort | `OnEventAsync` | Diese Methode kann überschrieben werden, um andere Arten von Ereignissen zu behandeln. |
| Anderer Aktivitätstyp empfangen | `OnUnrecognizedActivityTypeAsync` | Diese Methode kann überschrieben werden, um jeden Aktivitätstyp zu behandeln, andernfalls unbehandelt. |

#### <a name="teams-specific-activity-handlers"></a>Teams spezifischer Aktivitätshandler

Die `TeamsActivityHandler` Liste der Handler im Abschnitt "Bot Framework-Kernhandler" wird um Folgendes erweitert:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie im Kanal, der in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellt wurde](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter ["Kanal gelöscht](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)".|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der umbenannt wird. Weitere Informationen finden Sie unter ["Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)".|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Diese Methode kann überschrieben werden, um ein Teams Team zu verarbeiten, das umbenannt wird. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [conversation update events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler`auf. Die Methode kann überschrieben werden, um Mitglieder zu verarbeiten, die einem Team beitreten. Weitere Informationen finden Sie unter Teammitglieder, die in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügt wurden](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added).|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler`auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter ["Entfernte Teammitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) " in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Teams Aktivitäten aufrufen

Die Liste der vom Teams-Aktivitätshandler aufgerufenen `OnInvokeActivityAsync` Teams Aktivitätshandler umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Diese Methode wird aufgerufen, wenn eine Aktion zum Aufrufen einer Karte vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität Office 365 Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfungsstatusaktivität vom Connector empfangen wird. |
| aufgabe/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| Aufgabe/Absenden                     | `OnTeamsTaskModuleSubmitAsync`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul übermittelt wird. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt auch Aufrufaktivitäten speziell für Nachrichtenerweiterungen. Weitere Informationen finden Sie unter [Nachrichtenerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme der **Aktivitäten der hinzugefügten** und **entfernten** Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem nicht Teams Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten `ActivityHandler` Handler umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `onTurn` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Empfangene Nachrichtenaktivität | `onMessage` | Diese Methode hilft beim Behandeln einer `Message` Aktivität. |
| Unterhaltungsaktualisierungsaktivität empfangen | `onConversationUpdate` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer `ConversationUpdate` Aktivität beigetreten sind oder diese verlassen haben. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `onMembersAdded` | Diese Methode hilft bei der Behandlung von Mitgliedern, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Diese Methode hilft bei der Behandlung von Mitgliedern, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `onEvent` | Diese Methode ruft einen für den Ereignistyp spezifischen Handler für eine `Event` Aktivität auf. |
| Empfangene Token-Antwort-Ereignisaktivität | `onTokenResponseEvent` | Diese Methode hilft bei der Behandlung von Tokenantwortereignissen. |
| Anderer Aktivitätstyp empfangen | `onUnrecognizedActivityType` | Diese Methode hilft bei der Behandlung aller Aktivitätstypen, die andernfalls unbehandelt sind. |

#### <a name="teams-specific-activity-handlers"></a>Teams spezifischer Aktivitätshandler

Die `TeamsActivityHandler` Liste der Handler im Abschnitt "Bot Framework-Kernhandler" wird um Folgendes erweitert:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie im Kanal, der in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellt wurde](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter ["Kanal gelöscht](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)".|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der umbenannt wird. Weitere Informationen finden Sie unter ["Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)". |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Diese Methode kann überschrieben werden, um ein Teams Team zu verarbeiten, das umbenannt wird. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [conversation update events](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler`auf. Die Methode kann überschrieben werden, um Mitglieder zu verarbeiten, die einem Team beitreten. Weitere Informationen finden Sie unter Teammitglieder, die in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügt wurden](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added). |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler`auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter ["Entfernte Teammitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) " in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |

#### <a name="teams-invoke-activities"></a>Teams Aktivitäten aufrufen

Die Liste der vom Teams-Aktivitätshandler aufgerufenen `onInvokeActivity` Teams Aktivitätshandler umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Diese Methode wird aufgerufen, wenn eine Aktion zum Aufrufen einer Karte vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität Office 365 Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfungsstatusaktivität vom Connector empfangen wird. |
| aufgabe/fetch                      | `handleTeamsTaskModuleFetch`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| Aufgabe/Absenden                     | `handleTeamsTaskModuleSubmit`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul übermittelt wird. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt auch Aufrufaktivitäten speziell für Nachrichtenerweiterungen. Weitere Informationen finden Sie unter [Nachrichtenerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme der **Aktivitäten der hinzugefügten** und **entfernten** Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem nicht Teams Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten `ActivityHandler` Handler umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `on_turn` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Empfangene Nachrichtenaktivität | `on_message_activity` | Diese Methode kann überschrieben werden, um eine `Message` Aktivität zu behandeln. |
| Unterhaltungsaktualisierungsaktivität empfangen | `on_conversation_update_activity` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung beitreten oder diese verlassen. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `on_members_added_activity` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `on_members_removed_activity` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `on_event_activity` | Diese Methode ruft einen Handler auf, der für den Ereignistyp spezifisch ist. |
| Empfangene Token-Antwort-Ereignisaktivität | `on_token_response_event` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Ereignisaktivität ohne Tokenantwort | `on_event` | Diese Methode kann überschrieben werden, um andere Arten von Ereignissen zu behandeln. |
| Andere empfangene Aktivitätstypen | `on_unrecognized_activity_type` | Diese Methode kann überschrieben werden, um jede Art von Aktivität zu behandeln, die nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams spezifischer Aktivitätshandler

Die `TeamsActivityHandler` Liste der Handler wird aus dem Abschnitt mit den wichtigsten Bot Framework-Handlern erweitert, um Folgendes einzuschließen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie im Kanal, der in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellt wurde](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created). |
| channelDeleted | `on_teams_channel_deleted` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter ["Kanal gelöscht](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)".|
| channelRenamed | `on_teams_channel_renamed` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der umbenannt wird. Weitere Informationen finden Sie unter ["Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)".|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;`Diese Methode kann überschrieben werden, um ein Teams Team zu verarbeiten, das umbenannt wird. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [conversation update events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler`auf. Die Methode kann überschrieben werden, um Mitglieder zu verarbeiten, die einem Team beitreten. Weitere Informationen finden Sie unter Teammitglieder, die in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügt wurden](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added).|
| MembersRemoved | `on_teams_members_removed` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler`auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter ["Entfernte Teammitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) " in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Teams Aktivitäten aufrufen

Die Liste der vom Teams-Aktivitätshandler aufgerufenen `on_invoke_activity` Teams Aktivitätshandler umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Diese Methode wird aufgerufen, wenn eine Aktion zum Aufrufen einer Karte vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `on_teams_file_consent`            | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität Office 365 Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfungsstatusaktivität vom Connector empfangen wird. |
| aufgabe/fetch                      | `on_teams_task_module_fetch`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| Aufgabe/Absenden                     | `on_teams_task_module_submit`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul übermittelt wird. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt auch Aufrufaktivitäten speziell für Nachrichtenerweiterungen. Weitere Informationen finden Sie unter [Nachrichtenerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

---

---

Nachdem Sie sich nun mit Bot-Aktivitätshandlern vertraut machen, lassen Sie uns sehen, wie sich Bots je nach Unterhaltung und den empfangenen oder gesendeten Nachrichten unterschiedlich verhalten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Grundlagen zu Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
