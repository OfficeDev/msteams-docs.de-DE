---
title: Bot-Aktivitätenhandler
author: surbhigupta
description: Grundlegendes zu den Bot-Aktivitätenhandlern in Teams.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
keywords: Aktivitätenhandler Framework Bot Karte Zustimmung Kanal Ereignis
ms.openlocfilehash: 8bf1638274c8d83c8483df13556927d98b4d8cb5
ms.sourcegitcommit: 12510f34b00bfdd0b0e92d35c8dbe6ea1f6f0be2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2022
ms.locfileid: "66032921"
---
# <a name="bot-activity-handlers"></a>Bot-Aktivitätenhandler

Dieses Dokument baut auf dem Artikel über die [Wie Bots funktionieren](https://aka.ms/how-bots-work) in der Core [Bot Framework-Dokumentation](https://aka.ms/azure-bot-service-docs) auf. Der Hauptunterschied zwischen Bots, die für Microsoft Teams entwickelt wurden, und dem Core Bot Framework liegt in den Funktionen, die in Teams bereitgestellt werden.

Zum Organisieren der Unterhaltungslogik für Ihren Bot wird ein Aktivitätenhandler verwendet. Aktivitäten werden auf zwei Arten behandelt: mit Teams-Aktivitätenhandlern und Botlogik. Der Teams-Aktivitätenhandler fügt Unterstützung für Microsoft Teams-spezifische Ereignisse und Interaktionen hinzu. Das Botobjekt enthält die Unterhaltungslogik für einen Turn und macht einen Turnhandler verfügbar. Dies ist die Methode, die eingehende Aktivitäten vom Botadapter akzeptieren kann.

## <a name="teams-activity-handlers"></a>Teams Aktivitäten Handler

Der Teams-Aktivitätenhandler wird vom Aktivitätenhandler des Microsoft Bot Frameworks abgeleitet. Er leitet alle Teams-Aktivitäten weiter, bevor er die Behandlung von nicht Teams-spezifischen Aktivitäten zulässt.

Wenn ein Bot für Teams eine Aktivität empfängt, wird er an die Aktivitätshandler weitergeleitet. Alle Aktivitäten werden über einen Basishandler weitergeleitet, der als Turnhandler bezeichnet wird. Der Turnhandler ruft den erforderlichen Aktivitätenhandler auf, der für die Verarbeitung der empfangenen Aktivitätsart zuständig ist. Der Teams-Bot wird von der Klasse `TeamsActivityHandler` abgeleitet, die von der Klasse `ActivityHandler` des Bot Frameworks abgeleitet wird.

> [!NOTE]
> Wenn die Verarbeitung der Bot-Aktivität länger als 15 Sekunden dauert, Teams eine Wiederholungsanforderung an den Botendpunkt senden. Daher sehen Sie doppelte Anforderungen in Ihrem Bot.

# <a name="c"></a>[C#](#tab/csharp)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `OnMessageActivityAsync`-Aktivitätenhandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `OnConversationUpdateActivityAsync`. Der Teams-Aktivitätenhandler sucht zunächst nach Teams-spezifischen Ereignissen. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätenhandler des Bot Frameworks übergeben.

In der Teams-Aktivitätenhandlerklasse gibt es die zwei primären Teams-Aktivitätenhandler `OnConversationUpdateActivityAsync` und `OnInvokeActivityAsync`. `OnConversationUpdateActivityAsync` leitet alle Unterhaltungsaktualisierungsaktivitäten, und `OnInvokeActivityAsync` leitet alle Teams-Aufrufaktivitäten.

Um Ihre Logik für Teams-spezifische Aktivitätenhandler zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt [Botlogik](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die gewünschte Logik in ihrer Außerkraftsetzung hinzufügen.

Die Codeausschnitte für Teams-Aktivitätenhandler:

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

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `onMessage`-Aktivitätenhandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `dispatchConversationUpdateActivity`. Der Teams-Aktivitätenhandler sucht zunächst nach Teams-spezifischen Ereignissen. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätenhandler des Bot Frameworks übergeben.

In der Teams-Aktivitätenhandlerklasse gibt es die zwei primären Teams-Aktivitätenhandler `dispatchConversationUpdateActivity` und `onInvokeActivity`. `dispatchConversationUpdateActivity` leitet alle Unterhaltungsaktualisierungsaktivitäten, und `onInvokeActivity` leitet alle Teams-Aufrufaktivitäten.

Um Ihre Logik für Teams-spezifische Aktivitätenhandler zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt [Botlogik](#bot-logic) gezeigt. Definieren Sie Ihre Botlogik für diese Handler, und achten Sie daruf, dass Sie am Ende `next()` aufrufen. Durch Aufrufen `next()`stellen Sie sicher, dass der nächste Handler ausgeführt wird.

Die Codeausschnitte für Teams-Aktivitätenhandler:

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

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `on_message_activity`-Aktivitätenhandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `on_conversation_update_activity`. Der Teams-Aktivitätenhandler sucht zunächst nach Teams-spezifischen Ereignissen. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätenhandler des Bot Frameworks übergeben.

In der Teams-Aktivitätenhandlerklasse gibt es die zwei primären Teams-Aktivitätenhandler `on_conversation_update_activity` und `on_invoke_activity`. `on_conversation_update_activity` leitet alle Unterhaltungsaktualisierungsaktivitäten, und `on_invoke_activity` leitet alle Teams-Aufrufaktivitäten.

Um Ihre Logik für Teams-spezifische Aktivitätenhandler zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt [Botlogik](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die gewünschte Logik in ihrer Außerkraftsetzung hinzufügen.

---

## <a name="bot-logic"></a>Botlogik

Die Botlogik verarbeitet eingehende Aktivitäten aus einem oder mehreren Bot-Kanälen und generiert als Reaktion ausgehende Aktivitäten. Dies gilt immer noch für Bots, die von der Teams Aktivitätshandlerklasse abgeleitet wurden, die zuerst nach Teams Aktivitäten sucht. Nach der Überprüfung auf Teams-Aktivitäten übergibt sie alle anderen Aktivitäten an den Aktivitätenhandler des Bot Frameworks.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
>
>* Mit Ausnahme **hinzugefügter** und **entfernter** Teammitgliederaktivitäten funktionieren alle in diesem Abschnitt beschriebenen Aktivitätenhandler weiterhin wie bei einem Nicht-Teams-Bot.
>* Die `onInstallationUpdateActivityAsync()`-Methode wird verwendet, um Teams Locale abzurufen, während der Bot zu Teams hinzugefügt wird.

Aktivitätenhandler unterscheiden sich im Kontext eines Teams, in dem ein neues Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten `ActivityHandler` Handler umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `OnTurnAsync` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Nachrichtenaktivität empfangen | `OnMessageActivityAsync` | Diese Methode kann überschrieben werden, um eine `Message`-Aktivität zu behandeln. |
| Unterhaltungsaktualisierungsaktivität empfangen | `OnConversationUpdateActivityAsync` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer `ConversationUpdate`-Aktivität beigetreten sind oder diese verlassen haben. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `OnMembersAddedAsync` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Ereignisaktivität empfangen | `OnEventActivityAsync` | Diese Methode ruft bei einer `Event`-Aktivität einen für den Ereignistyp spezifischen Handler auf. |
| Token-Antwort-Ereignisaktivität empfangen | `OnTokenResponseEventAsync` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Ereignisaktivität ohne Tokenantwort empfangen | `OnEventAsync` | Diese Methode kann überschrieben werden, um andere Arten von Ereignissen zu behandeln. |
| Anderer Aktivitätstyp empfangen | `OnUnrecognizedActivityTypeAsync` | Diese Methode kann überschrieben werden, um jeden Aktivitätstyp zu behandeln, andernfalls unbehandelt. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätenhandler

Der `TeamsActivityHandler` erweitert die Liste der Handler im Abschnitt „Core Bot Framework-Handler“ um Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der erstellt wird. Weitere Informationen finden Sie siehe [Kanal erstellt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| ChannelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der gelöscht wird. Weitere Informationen finden Sie siehe [Kanal gelöscht](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der umbenannt wird. Weitere Informationen finden Sie siehe [Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Diese Methode kann überschrieben werden, um ein Team in Teams zu behandeln, das umbenannt wird. Weitere Informationen finden Sie siehe [Team umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft im `ActivityHandler` die Methode `OnMembersAddedAsync` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie siehe [Teammitglieder hinzugefügt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft im `ActivityHandler` die Methode `OnMembersRemovedAsync` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie siehe [Teammitglieder entfernt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Aufrufaktivitäten in Teams

Die Liste der vom Teams-Aktivitätshandler aufgerufenen `OnInvokeActivityAsync` Teams Aktivitätshandler umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Diese Methode wird aufgerufen, wenn eine Aktion zum Aufrufen einer Karte vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität Office 365 Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfungsstatusaktivität vom Connector empfangen wird. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um die Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| task/submit                     | `OnTeamsTaskModuleSubmitAsync`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um die Logik bereitzustellen, wenn ein Aufgabenmodul übermittelt wird. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt speziell für Nachrichtenerweiterungen auch Aufrufaktivitäten. Weitere Informationen finden Sie unter [Nachrichtenerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme **hinzugefügter** und **entfernter** Teammitgliederaktivitäten funktionieren alle in diesem Abschnitt beschriebenen Aktivitätenhandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätenhandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten `ActivityHandler` Handler umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `onTurn` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Nachrichtenaktivität empfangen | `onMessage` | Diese Methode hilft beim Behandeln einer `Message`-Aktivität. |
| Unterhaltungsaktualisierungsaktivität empfangen | `onConversationUpdate` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer `ConversationUpdate`-Aktivität beigetreten sind oder diese verlassen haben. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `onMembersAdded` | Diese Methode hilft bei der Behandlung von Mitgliedern, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Diese Methode hilft bei der Behandlung von Mitgliedern, die eine Unterhaltung verlassen. |
| Ereignisaktivität empfangen | `onEvent` | Diese Methode ruft bei einer `Event`-Aktivität einen für den Ereignistyp spezifischen Handler auf. |
| Token-Antwort-Ereignisaktivität empfangen | `onTokenResponseEvent` | Diese Methode hilft bei der Behandlung von Tokenantwortereignissen. |
| Anderer Aktivitätstyp empfangen | `onUnrecognizedActivityType` | Diese Methode hilft bei der Behandlung aller Aktivitätstypen, die andernfalls unbehandelt sind. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätenhandler

Der `TeamsActivityHandler` erweitert die Liste der Handler im Abschnitt „Core Bot Framework-Handler“ um Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der erstellt wird. Weitere Informationen finden Sie siehe [Kanal erstellt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| ChannelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der gelöscht wird. Weitere Informationen finden Sie siehe [Kanal gelöscht](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der umbenannt wird. Weitere Informationen finden Sie siehe [Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Diese Methode kann überschrieben werden, um ein Team in Teams zu behandeln, das umbenannt wird. Weitere Informationen finden Sie siehe [Team umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft im `ActivityHandler` die Methode `OnMembersAddedAsync` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie siehe [Teammitglieder hinzugefügt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft im `ActivityHandler` die Methode `OnMembersRemovedAsync` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie siehe [Teammitglieder entfernt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |

#### <a name="teams-invoke-activities"></a>Aufrufaktivitäten in Teams

Die Liste der vom Teams-Aktivitätshandler aufgerufenen `onInvokeActivity` Teams Aktivitätshandler umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Diese Methode wird aufgerufen, wenn eine Aktion zum Aufrufen einer Karte vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität Office 365 Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfungsstatusaktivität vom Connector empfangen wird. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um die Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| task/submit                     | `handleTeamsTaskModuleSubmit`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um die Logik bereitzustellen, wenn ein Aufgabenmodul übermittelt wird. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt speziell für Nachrichtenerweiterungen auch Aufrufaktivitäten. Weitere Informationen finden Sie unter [Nachrichtenerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme **hinzugefügter** und **entfernter** Teammitgliederaktivitäten funktionieren alle in diesem Abschnitt beschriebenen Aktivitätenhandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätenhandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten `ActivityHandler` Handler umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `on_turn` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Nachrichtenaktivität empfangen | `on_message_activity` | Diese Methode kann überschrieben werden, um eine `Message`-Aktivität zu behandeln. |
| Unterhaltungsaktualisierungsaktivität empfangen | `on_conversation_update_activity` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung beitreten oder diese verlassen. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `on_members_added_activity` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `on_members_removed_activity` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Ereignisaktivität empfangen | `on_event_activity` | Diese Methode ruft einen Handler auf, der für den Ereignistyp spezifisch ist. |
| Token-Antwort-Ereignisaktivität empfangen | `on_token_response_event` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Ereignisaktivität ohne Tokenantwort empfangen | `on_event` | Diese Methode kann überschrieben werden, um andere Arten von Ereignissen zu behandeln. |
| Andere Aktivitätstypen empfangen | `on_unrecognized_activity_type` | Diese Methode kann überschrieben werden, um jede Art von Aktivität zu behandeln, die nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätenhandler

Der `TeamsActivityHandler` erweitert die Liste der Handler vom Abschnitt „Core Bot Framework-Handler“ um Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der erstellt wird. Weitere Informationen finden Sie siehe [Kanal erstellt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| ChannelDeleted | `on_teams_channel_deleted` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der gelöscht wird. Weitere Informationen finden Sie siehe [Kanal gelöscht](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `on_teams_channel_renamed` | Diese Methode kann überschrieben werden, um einen Teams-Kanal zu behandeln, der umbenannt wird. Weitere Informationen finden Sie siehe [Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Diese Methode kann überschrieben werden, um ein Team in Teams zu behandeln, das umbenannt wird. Weitere Informationen finden Sie siehe [Team umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Diese Methode ruft im `ActivityHandler` die Methode `OnMembersAddedAsync` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie siehe [Teammitglieder hinzugefügt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `on_teams_members_removed` | Diese Methode ruft im `ActivityHandler` die Methode `OnMembersRemovedAsync` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie siehe [Teammitglieder entfernt](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) unter [Aktualisierungsereignisse in Unterhaltungen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Aufrufaktivitäten in Teams

Die Liste der vom Teams-Aktivitätshandler aufgerufenen `on_invoke_activity` Teams Aktivitätshandler umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Diese Methode wird aufgerufen, wenn eine Aktion zum Aufrufen einer Karte vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `on_teams_file_consent`            | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Diese Methode wird aufgerufen, wenn eine Dateizustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität Office 365 Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfungsstatusaktivität vom Connector empfangen wird. |
| task/fetch                      | `on_teams_task_module_fetch`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um die Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| task/submit                     | `on_teams_task_module_submit`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um die Logik bereitzustellen, wenn ein Aufgabenmodul übermittelt wird. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt speziell für Nachrichtenerweiterungen auch Aufrufaktivitäten. Weitere Informationen finden Sie unter [Nachrichtenerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

---

---

Nachdem Sie sich nun mit Bot-Aktivitätshandlern vertraut machen, lassen Sie uns sehen, wie sich Bots je nach Unterhaltung und den empfangenen oder gesendeten Nachrichten unterschiedlich verhalten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Grundlagen zu Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
