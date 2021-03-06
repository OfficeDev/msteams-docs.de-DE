---
title: Bot-Aktivitätenhandler
author: surbhigupta
description: Grundlegendes zu den Bot-Aktivitätshandlern in Teams.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 4ecc40abca84466887466ef6a25ab6e57a38328c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069034"
---
# <a name="bot-activity-handlers"></a>Bot-Aktivitätenhandler

Dieses Dokument baut auf dem Artikel zur [Funktionsweise von Bots](https://aka.ms/how-bots-work) in der Grundlegenden [Bot Framework-Dokumentation](https://aka.ms/azure-bot-service-docs)auf. Der Hauptunterschied zwischen Bots, die für Microsoft Teams entwickelt wurden, und dem Core Bot Framework sind die Features, die in Teams bereitgestellt werden.

Um die Unterhaltungslogik für Ihren Bot zu organisieren, wird ein Aktivitätshandler verwendet. Aktivitäten werden mit Teams Aktivitätshandlern und Botlogik auf zwei Arten behandelt. Der Teams-Aktivitätshandler fügt Unterstützung für Microsoft Teams-spezifische Ereignisse und Interaktionen hinzu. Das Bot-Objekt enthält die unterhaltungsbezogene Logik oder Logik für eine Drehung und macht einen Turnhandler verfügbar, der die Methode ist, die eingehende Aktivitäten vom Botadapter akzeptieren kann.

## <a name="teams-activity-handlers"></a>Teams-Aktivitätshandler

Teams Aktivitätshandler wird vom Aktivitätshandler Microsoft Bot Framework abgeleitet. Es leitet alle Teams Aktivitäten weiter, bevor nicht Teams bestimmte Aktivitäten verarbeitet werden können.

Wenn ein Bot für Teams eine Aktivität empfängt, wird er an die Aktivitätshandler weitergeleitet. Alle Aktivitäten werden über einen Basishandler weitergeleitet, der als Turnhandler bezeichnet wird. Der Turnhandler ruft den erforderlichen Aktivitätshandler auf, um empfangene Aktivitäten zu verwalten. Der Teams Bot wird von `TeamsActivityHandler` der Klasse abgeleitet, die von der Klasse des Bot-Frameworks abgeleitet `ActivityHandler` wird.

# <a name="c"></a>[C#](#tab/csharp)

Bots werden mithilfe des Bot Frameworks erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `OnMessageActivityAsync` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `OnConversationUpdateActivityAsync` . Der Teams-Aktivitätshandler überprüft zuerst nach Teams bestimmten Ereignissen. Wenn keine Ereignisse gefunden werden, werden diese an den Aktivitätshandler des Bot-Frameworks übergeben.

In der Teams Aktivitätshandlerklasse gibt es zwei primäre Teams Aktivitätshandler `OnConversationUpdateActivityAsync` und `OnInvokeActivityAsync` . `OnConversationUpdateActivityAsync`leitet alle Unterhaltungsaktualisierungsaktivitäten weiter und `OnInvokeActivityAsync` leitet alle Teams Aufrufen von Aktivitäten weiter.

Um Ihre Logik für Teams bestimmten Aktivitätshandlern zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt ["Botlogik"](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die gewünschte Logik in der Außerkraftsetzung hinzufügen.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Bots werden mithilfe des Bot Frameworks erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `onMessage` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `dispatchConversationUpdateActivity` . Der Teams-Aktivitätshandler überprüft zuerst nach Teams bestimmten Ereignissen. Wenn keine Ereignisse gefunden werden, werden diese an den Aktivitätshandler des Bot-Frameworks übergeben.

In der Teams Aktivitätshandlerklasse gibt es zwei primäre Teams Aktivitätshandler `dispatchConversationUpdateActivity` und `onInvokeActivity` . `dispatchConversationUpdateActivity`leitet alle Unterhaltungsaktualisierungsaktivitäten weiter und `onInvokeActivity` leitet alle Teams Aufrufen von Aktivitäten weiter.

Um Ihre Logik für Teams bestimmten Aktivitätshandlern zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt ["Botlogik"](#bot-logic) gezeigt. Definieren Sie Ihre Botlogik für diese Handler, und rufen Sie `next()` sie dann am Ende auf. Durch Aufrufen `next()` stellen Sie sicher, dass der nächste Handler ausgeführt wird.

# <a name="python"></a>[Python](#tab/python)

Bots werden mithilfe des Bot Frameworks erstellt. Wenn die Bots eine Nachrichtenaktivität erhalten, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `on_message_activity` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `on_conversation_update_activity` . Der Teams-Aktivitätshandler überprüft zuerst nach Teams bestimmten Ereignissen. Wenn keine Ereignisse gefunden werden, werden diese an den Aktivitätshandler des Bot-Frameworks übergeben.

In der Teams Aktivitätshandlerklasse gibt es zwei primäre Teams Aktivitätshandler `on_conversation_update_activity` und `on_invoke_activity` . `on_conversation_update_activity`leitet alle Unterhaltungsaktualisierungsaktivitäten weiter und `on_invoke_activity` leitet alle Teams Aufrufen von Aktivitäten weiter.

Um Ihre Logik für Teams bestimmten Aktivitätshandlern zu implementieren, müssen Sie die Methoden in Ihrem Bot überschreiben, wie im Abschnitt ["Botlogik"](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die gewünschte Logik in der Außerkraftsetzung hinzufügen.

---

## <a name="bot-logic"></a>Botlogik

Die Botlogik verarbeitet eingehende Aktivitäten von einem oder mehreren Ihrer Botkanäle und generiert als Reaktion ausgehende Aktivitäten. Dies gilt weiterhin für Bots, die von der Teams Aktivitätshandlerklasse abgeleitet sind, die zuerst nach Teams Aktivitäten sucht. Nach der Überprüfung auf Teams Aktivitäten werden alle anderen Aktivitäten an den Aktivitätshandler des Bot-Frameworks übergeben.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme der **hinzugefügten** und **entfernten** Aktivitäten von Mitgliedern funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem dem Team ein neues Mitglied anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten Handler `ActivityHandler` umfasst Folgendes:

| Event | Handler | Beschreibung |
| :-- | :-- | :-- |
| Empfangener Aktivitätstyp | `OnTurnAsync` | Diese Methode ruft basierend auf dem Typ der empfangenen Aktivität einen der anderen Handler auf. |
| Empfangene Nachrichtenaktivität | `OnMessageActivityAsync` | Diese Methode kann überschrieben werden, um eine Aktivität zu `Message` behandeln. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `OnConversationUpdateActivityAsync` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung für eine Aktivität beigetreten sind oder diese verlassen `ConversationUpdate` haben. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `OnMembersAddedAsync` | Diese Methode kann überschrieben werden, um Mitglieder zu verarbeiten, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Diese Methode kann überschrieben werden, um Elemente zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `OnEventActivityAsync` | Diese Methode ruft einen für den Ereignistyp spezifischen Handler für eine `Event` Aktivität auf. |
| Empfangene Token-Antwort-Ereignisaktivität | `OnTokenResponseEventAsync` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Ereignisaktivität ohne Tokenantwort | `OnEventAsync` | Diese Methode kann überschrieben werden, um andere Ereignistypen zu behandeln. |
| Anderer empfangener Aktivitätstyp | `OnUnrecognizedActivityTypeAsync` | Diese Methode kann überschrieben werden, um alle Aktivitätstypen zu behandeln, die andernfalls nicht behandelt werden. |

#### <a name="teams-specific-activity-handlers"></a>Teams bestimmten Aktivitätshandlern

Die `TeamsActivityHandler` Liste der Handler im Core Bot Framework-Handlerabschnitt wird erweitert, um Folgendes einzuschließen:

| Event | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie im Kanal, der in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellt wurde.](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen Teams zu löschenden Kanal zu verarbeiten. Weitere Informationen finden Sie unter "In [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal".](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted)|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der umbenannt wird. Weitere Informationen finden Sie unter ["Kanal umbenannt"](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Diese Methode kann überschrieben werden, um ein Teams Team zu verarbeiten, das umbenannt wird. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [conversation update events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter Teammitglieder, die in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added)|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter Teammitglieder, die in [Aktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)für [Unterhaltungen entfernt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed)|

#### <a name="teams-invoke-activities"></a>Teams Aufrufen von Aktivitäten

Die Liste der vom `OnInvokeActivityAsync` Teams-Aktivitätshandler aufgerufenen Teams Aktivitätshandler umfasst Folgendes:

| Aufrufen von Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität der O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfung der Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| task/submit                     | `OnTeamsTaskModuleSubmitAsync`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Beim Senden eines Aufgabenmoduls Logik bereitzustellen. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch Aufrufaktivitäten, die für Messaging-Erweiterungen spezifisch sind. Weitere Informationen finden Sie unter ["Messaging-Erweiterungen".](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme der **hinzugefügten** und **entfernten** Aktivitäten von Mitgliedern funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten Handler `ActivityHandler` umfasst Folgendes:

| Event | Handler | Beschreibung |
| :-- | :-- | :-- |
| Empfangener Aktivitätstyp | `onTurn` | Diese Methode ruft basierend auf dem Typ der empfangenen Aktivität einen der anderen Handler auf. |
| Empfangene Nachrichtenaktivität | `onMessage` | Diese Methode hilft bei der Verarbeitung einer `Message` Aktivität. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `onConversationUpdate` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung für eine Aktivität beigetreten sind oder diese verlassen `ConversationUpdate` haben. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `onMembersAdded` | Diese Methode hilft bei der Behandlung von Mitgliedern, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Diese Methode hilft bei der Behandlung von Mitgliedern, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `onEvent` | Diese Methode ruft einen für den Ereignistyp spezifischen Handler für eine `Event` Aktivität auf. |
| Empfangene Token-Antwort-Ereignisaktivität | `onTokenResponseEvent` | Diese Methode hilft bei der Behandlung von Tokenantwortereignissen. |
| Anderer empfangener Aktivitätstyp | `onUnrecognizedActivityType` | Diese Methode hilft bei der Behandlung aller Aktivitätstypen, die andernfalls nicht behandelt werden. |

#### <a name="teams-specific-activity-handlers"></a>Teams bestimmten Aktivitätshandlern

Die `TeamsActivityHandler` Liste der Handler im Core Bot Framework-Handlerabschnitt wird erweitert, um Folgendes einzuschließen:

| Event | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie im Kanal, der in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellt wurde.](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen Teams zu löschenden Kanal zu verarbeiten. Weitere Informationen finden Sie unter "In [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal".](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted)|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der umbenannt wird. Weitere Informationen finden Sie unter ["Kanal umbenannt"](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Diese Methode kann überschrieben werden, um ein Teams Team zu verarbeiten, das umbenannt wird. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [conversation update events](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter Teammitglieder, die in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter Teammitglieder, die in [Aktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)für [Unterhaltungen entfernt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) |

#### <a name="teams-invoke-activities"></a>Teams Aufrufen von Aktivitäten

Die Liste der vom `onInvokeActivity` Teams-Aktivitätshandler aufgerufenen Teams Aktivitätshandler umfasst Folgendes:

| Aufrufen von Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität der O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfung der Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| task/submit                     | `handleTeamsTaskModuleSubmit`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Beim Senden eines Aufgabenmoduls Logik bereitzustellen. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt auch Aufrufaktivitäten, die für Messaging-Erweiterungen spezifisch sind. Weitere Informationen finden Sie unter ["Messaging-Erweiterungen".](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework-Handler

>[!NOTE]
> Mit Ausnahme der **hinzugefügten** und **entfernten** Aktivitäten von Mitgliedern funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten Handler `ActivityHandler` umfasst Folgendes:

| Event | Handler | Beschreibung |
| :-- | :-- | :-- |
| Empfangener Aktivitätstyp | `on_turn` | Diese Methode ruft basierend auf dem Typ der empfangenen Aktivität einen der anderen Handler auf. |
| Empfangene Nachrichtenaktivität | `on_message_activity` | Diese Methode kann überschrieben werden, um eine Aktivität zu `Message` behandeln. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `on_conversation_update_activity` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung beitreten oder diese verlassen. |
| Nicht-Bot-Mitglieder sind der Unterhaltung beigetreten | `on_members_added_activity` | Diese Methode kann überschrieben werden, um Mitglieder zu verarbeiten, die an einer Unterhaltung teilnehmen. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `on_members_removed_activity` | Diese Methode kann überschrieben werden, um Elemente zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `on_event_activity` | Diese Methode ruft einen Handler auf, der für den Typ des Ereignisses spezifisch ist. |
| Empfangene Token-Antwort-Ereignisaktivität | `on_token_response_event` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Ereignisaktivität ohne Tokenantwort | `on_event` | Diese Methode kann überschrieben werden, um andere Ereignistypen zu behandeln. |
| Andere empfangene Aktivitätstypen | `on_unrecognized_activity_type` | Diese Methode kann überschrieben werden, um jede Art von Aktivität zu behandeln, die nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams bestimmten Aktivitätshandlern

Die `TeamsActivityHandler` Liste der Handler aus dem Core Bot Framework-Handlerabschnitt wird um Folgendes erweitert:

| Event | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie im Kanal, der in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellt wurde.](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) |
| channelDeleted | `on_teams_channel_deleted` | Diese Methode kann überschrieben werden, um einen Teams zu löschenden Kanal zu verarbeiten. Weitere Informationen finden Sie unter "In [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal".](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted)|
| channelRenamed | `on_teams_channel_renamed` | Diese Methode kann überschrieben werden, um einen Teams Kanal zu verarbeiten, der umbenannt wird. Weitere Informationen finden Sie unter ["Kanal umbenannt"](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;`Diese Methode kann überschrieben werden, um ein Teams Team zu verarbeiten, das umbenannt wird. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [conversation update events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter Teammitglieder, die in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added)|
| MembersRemoved | `on_teams_members_removed` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter Teammitglieder, die in [Aktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events)für [Unterhaltungen entfernt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed)|

#### <a name="teams-invoke-activities"></a>Teams Aufrufen von Aktivitäten

Die Liste der vom `on_invoke_activity` Teams-Aktivitätshandler aufgerufenen Teams Aktivitätshandler umfasst Folgendes:

| Aufrufen von Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `on_teams_file_consent`            | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Diese Methode wird aufgerufen, wenn eine Dateigenehmigungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität der O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Diese Methode wird aufgerufen, wenn eine signIn-Überprüfung der Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `on_teams_task_module_fetch`        | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Logik bereitzustellen, wenn ein Aufgabenmodul abgerufen wird. |
| task/submit                     | `on_teams_task_module_submit`       | Diese Methode kann in einer abgeleiteten Klasse überschrieben werden, um Beim Senden eines Aufgabenmoduls Logik bereitzustellen. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten gelten für Unterhaltungs-Bots in Teams. Das Bot Framework SDK unterstützt auch Aufrufaktivitäten, die für Messaging-Erweiterungen spezifisch sind. Weitere Informationen finden Sie unter ["Messaging-Erweiterungen".](https://aka.ms/azure-bot-what-are-messaging-extensions)

---

* * *

Nachdem Sie sich nun mit Bot-Aktivitätshandlern vertraut machen, können wir sehen, wie sich Bots je nach Unterhaltung und den empfangenen oder gesendeten Nachrichten unterschiedlich verhalten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Grundlagen zu Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
