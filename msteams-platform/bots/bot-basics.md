---
title: Botgrundkenntnisse
author: clearab
description: Grundlegendes zu Bots in Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 3c4e707fa4677c2441f348e8d09ecf4428ef1296
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014502"
---
# <a name="bot-basics"></a>Botgrundkenntnisse

Dieses Dokument enthält eine Einführung in Bots in Microsoft Teams, die auf dem Artikel "Funktionsweise von [Bots](https://aka.ms/how-bots-work) in der grundlegenden [Bot Framework-Dokumentation" basiert.](https://aka.ms/azure-bot-service-docs) Der Hauptunterschied zwischen Bots, die für Microsoft Teams entwickelt wurden, und dem zentralen Bot Framework liegt in den In Teams bereitgestellten Features.

## <a name="teams-activity-handlers"></a>Teams-Aktivitätshandler

Der Microsoft Teams-Aktivitätshandler wird vom Aktivitätshandler von Microsoft Bot Framework abgeleitet. Es leitet alle Teams-Aktivitäten weiter, bevor alle nicht teamsspezifischen Aktivitäten behandelt werden können.

Wenn ein Bot für Teams eine Aktivität empfängt, wird er an die *Aktivitätshandler geleitet.* Alle Aktivitäten werden über einen Basishandler geroutet, der als *"Turn Handler" bezeichnet wird.* Der *Turnhandler ruft* den erforderlichen Aktivitätshandler auf, um empfangene Aktivitäten zu verwalten. Der Teams Bot wird von der Klasse abgeleitet, die von der Klasse des `TeamsActivityHandler` Bot Frameworks `ActivityHandler` abgeleitet ist.

# <a name="c"></a>[C#](#tab/csharp)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität empfangen, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `OnMessageActivityAsync` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `OnConversationUpdateActivityAsync` . Der Aktivitätshandler von Teams überprüft zunächst auf teamsspezifische Ereignisse. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot Frameworks übergeben.

In der Aktivitätshandlerklasse von Teams gibt es zwei primäre Teams-Aktivitätshandler `OnConversationUpdateActivityAsync` und `OnInvokeActivityAsync` . `OnConversationUpdateActivityAsync` leitet alle Unterhaltungsaktualisierungsaktivitäten und `OnInvokeActivityAsync` alle von Teams aufgerufenen Aktivitäten um.

Um Ihre Logik für teams-spezifische Aktivitätshandler zu implementieren, müssen Sie die Methoden in Ihrem Bot außer Kraft setzen, wie im Abschnitt ["Botlogik"](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die logik, die Sie für die Außerkraftsetzung verwenden möchten, hinzufügen.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität empfangen, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `onMessage` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `dispatchConversationUpdateActivity` . Der Aktivitätshandler von Teams überprüft zunächst auf teamsspezifische Ereignisse. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot Frameworks übergeben.

In der Aktivitätshandlerklasse von Teams gibt es zwei primäre Teams-Aktivitätshandler `dispatchConversationUpdateActivity` und `onInvokeActivity` . `dispatchConversationUpdateActivity` leitet alle Unterhaltungsaktualisierungsaktivitäten und `onInvokeActivity` alle von Teams aufgerufenen Aktivitäten um.

Um Ihre Logik für teams-spezifische Aktivitätshandler zu implementieren, müssen Sie die Methoden in Ihrem Bot außer Kraft setzen, wie im Abschnitt ["Botlogik"](#bot-logic) gezeigt. Definieren Sie Ihre Botlogik für diese Handler, und rufen Sie am Ende **`next()` unbedingt auf.** Durch aufrufen `next()` stellen Sie sicher, dass der nächste Handler ausgeführt wird.

# <a name="python"></a>[Python](#tab/python)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität empfangen, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `on_message_activity` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `on_conversation_update_activity` . Der Aktivitätshandler von Teams überprüft zuerst auf teamsspezifische Ereignisse. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot Frameworks übergeben.

In der Aktivitätshandlerklasse von Teams gibt es zwei primäre Teams-Aktivitätshandler `on_conversation_update_activity` und `on_invoke_activity` . `on_conversation_update_activity` leitet alle Unterhaltungsaktualisierungsaktivitäten `on_invoke_activity` und alle von Teams aufgerufenen Aktivitäten um.

Um Ihre Logik für teams-spezifische Aktivitätshandler zu implementieren, müssen Sie die Methoden in Ihrem Bot außer Kraft setzen, wie im Abschnitt ["Botlogik"](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler. Daher müssen Sie die Logik, die Sie für die Außerkraftsetzung verwenden möchten, hinzufügen.

---

## <a name="bot-logic"></a>Botlogik

Die Botlogik verarbeitet eingehende Aktivitäten von einem oder mehreren Ihrer Botkanäle und generiert als Reaktion ausgehende Aktivitäten. Dies gilt weiterhin für Bots, die von der Aktivitätshandlerklasse von Teams abgeleitet werden und zuerst nach Aktivitäten von Teams sucht. Nach der Überprüfung auf Teams-Aktivitäten werden alle anderen Aktivitäten an den Aktivitätshandler des Bot Frameworks übergeben.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework Handler

>[!NOTE]
> Mit Ausnahme der  *Aktivitäten hinzugefügter* und entfernter Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem dem Team ein neues Mitglied anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten Handler `ActivityHandler` umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `OnTurnAsync` | Diese Methode ruft basierend auf dem Typ der empfangenen Aktivität einen der anderen Handler auf. |
| Empfangene Nachrichtenaktivität | `OnMessageActivityAsync` | Diese Methode kann überschrieben werden, um eine Aktivität zu `Message` verarbeiten. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `OnConversationUpdateActivityAsync` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer Aktivität beigetreten sind oder diese verlassen `ConversationUpdate` haben. |
| Nicht-Bot-Mitglieder, die der Unterhaltung beigetreten sind | `OnMembersAddedAsync` | Diese Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Diese Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `OnEventActivityAsync` | Diese Methode ruft einen für den Ereignistyp spezifischen Handler für eine Aktivität `Event` auf. |
| Empfangene Tokenantwortereignisaktivität | `OnTokenResponseEventAsync` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Nicht-Token-Antwort-Ereignisaktivität | `OnEventAsync` | Diese Methode kann überschrieben werden, um andere Ereignistypen zu behandeln. |
| Anderer empfangener Aktivitätstyp | `OnUnrecognizedActivityTypeAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen beliebigen Aktivitätstyp zu behandeln, der andernfalls nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätshandler

Die Liste der Handler im Abschnitt "Core Bot Framework handlers" wird um `TeamsActivityHandler` Folgendes erweitert:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen erstellten Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter ["Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) erstellt in [Unterhaltungsaktualisierungsereignissen".](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen zu löschenden Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter ["Kanal gelöscht"](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen umbenannten Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter ["Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) umbenannt" in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Diese Methode kann außer Kraft gesetzt werden, um ein umbenanntes Teams-Team zu verarbeiten. Weitere Informationen finden Sie unter ["Team umbenannt"](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter ["In Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) [hinzugefügte Teammitglieder".](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter ["In Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) [entfernte Teammitglieder".](https://aka.ms/azure-bot-subscribe-to-conversation-events)|

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Die Liste der Teams-Aktivitätshandler, die vom Aktivitätshandler von Teams aufgerufen `OnInvokeActivityAsync` werden, umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Diese Methode wird aufgerufen, wenn eine Aktivität der Datei-Zustimmungskarte vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität der O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Diese Methode wird aufgerufen, wenn ein signIn überprüft, ob die Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Abrufen eines Aufgabenmoduls zur Verfügung zu stellen. |
| task/submit                     | `OnTeamsTaskModuleSubmitAsync`       | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Übermittelt eines Aufgabenmoduls zur Verfügung zu stellen. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten sind für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch das Aufrufen von Aktivitäten speziell für Messagingerweiterungen. Weitere Informationen finden Sie unter ["Was sind Messagingerweiterungen".](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework Handler

>[!NOTE]
> Mit Ausnahme der  *Aktivitäten hinzugefügter* und entfernter Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten Handler `ActivityHandler` umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `onTurn` | Diese Methode ruft basierend auf dem Typ der empfangenen Aktivität einen der anderen Handler auf. |
| Empfangene Nachrichtenaktivität | `onMessage` | Diese Methode hilft bei der Behandlung einer `Message` Aktivität. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `onConversationUpdate` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer Aktivität beigetreten sind oder diese verlassen `ConversationUpdate` haben. |
| Nicht-Bot-Mitglieder, die der Unterhaltung beigetreten sind | `onMembersAdded` | Diese Methode hilft bei der Behandlung von Mitgliedern, die einer Unterhaltung beitreten. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Diese Methode hilft bei der Behandlung von Mitgliedern, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `onEvent` | Diese Methode ruft einen für den Ereignistyp spezifischen Handler für eine Aktivität `Event` auf. |
| Empfangene Tokenantwortereignisaktivität | `onTokenResponseEvent` | Diese Methode hilft bei der Behandlung von Tokenantwortereignissen. |
| Anderer empfangener Aktivitätstyp | `onUnrecognizedActivityType` | Diese Methode hilft bei der Behandlung beliebiger Aktivitätstypen, die andernfalls nicht behandelt werden. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätshandler

Die `TeamsActivityHandler` Liste der Handler im Abschnitt "Core Bot Framework handlers" erweitert die folgenden Handler:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen erstellten Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter ["Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) erstellt in [Unterhaltungsaktualisierungsereignissen".](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen zu löschenden Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter ["Kanal gelöscht"](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen umbenannten Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter ["Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) umbenannt" in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Diese Methode kann außer Kraft gesetzt werden, um ein umbenanntes Teams-Team zu verarbeiten. Weitere Informationen finden Sie unter ["Team umbenannt"](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter ["In Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) [hinzugefügte Teammitglieder".](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter ["In Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) [entfernte Teammitglieder".](https://aka.ms/azure-bot-subscribe-to-conversation-events) |

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Die Liste der Teams-Aktivitätshandler, die vom Aktivitätshandler von Teams aufgerufen `onInvokeActivity` werden, umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Diese Methode wird aufgerufen, wenn eine Aktivität der Datei-Zustimmungskarte vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität der O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Diese Methode wird aufgerufen, wenn ein signIn überprüft, ob die Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Abrufen eines Aufgabenmoduls zu liefern. |
| task/submit                     | `handleTeamsTaskModuleSubmit`       | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Übermittelt eines Aufgabenmoduls zur Verfügung zu stellen. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten sind für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch das Aufrufen von Aktivitäten speziell für Messagingerweiterungen. Weitere Informationen finden Sie unter ["Was sind Messagingerweiterungen".](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework Handler

>[!NOTE]
> Mit Ausnahme der  *Aktivitäten hinzugefügter* und entfernter Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der definierten Handler `ActivityHandler` umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `on_turn` | Diese Methode ruft basierend auf dem Typ der empfangenen Aktivität einen der anderen Handler auf. |
| Empfangene Nachrichtenaktivität | `on_message_activity` | Diese Methode kann überschrieben werden, um eine Aktivität zu `Message` verarbeiten. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `on_conversation_update_activity` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung beitreten oder diese verlassen. |
| Nicht-Bot-Mitglieder, die der Unterhaltung beigetreten sind | `on_members_added_activity` | Diese Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `on_members_removed_activity` | Diese Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `on_event_activity` | Diese Methode ruft einen Handler auf, der für den Ereignistyp spezifisch ist. |
| Empfangene Tokenantwortereignisaktivität | `on_token_response_event` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Nicht-Token-Antwort-Ereignisaktivität | `on_event` | Diese Methode kann außer Kraft gesetzt werden, um andere Ereignistypen zu behandeln. |
| Andere empfangene Aktivitätstypen | `on_unrecognized_activity_type` | Diese Methode kann außer Kraft gesetzt werden, um jede Art von Aktivität zu verarbeiten, die nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätshandler

Die `TeamsActivityHandler` Liste der Handler aus dem Abschnitt "Core Bot Framework handlers" erweitert die folgenden Handler:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Diese Methode kann außer Kraft gesetzt werden, um einen erstellten Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter ["Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) erstellt in [Unterhaltungsaktualisierungsereignissen".](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `on_teams_channel_deleted` | Diese Methode kann außer Kraft gesetzt werden, um einen zu löschenden Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter ["Kanal gelöscht"](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| channelRenamed | `on_teams_channel_renamed` | Diese Methode kann außer Kraft gesetzt werden, um einen umbenannten Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter ["Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) umbenannt" in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Diese Methode kann außer Kraft gesetzt werden, um ein umbenanntes Teams-Team zu behandeln. Weitere Informationen finden Sie unter ["Team umbenannt"](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [Unterhaltungsaktualisierungsereignissen.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersAdded | `on_teams_members_added` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter ["In Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) [hinzugefügte Teammitglieder".](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersRemoved | `on_teams_members_removed` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann außer Kraft gesetzt werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter ["In Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) [entfernte Teammitglieder".](https://aka.ms/azure-bot-subscribe-to-conversation-events)|

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Die Liste der Teams-Aktivitätshandler, die vom Aktivitätshandler von Teams aufgerufen `on_invoke_activity` werden, umfasst Folgendes:

| Aufruftypen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `on_teams_file_consent`            | Diese Methode wird aufgerufen, wenn eine Aktivität der Datei-Zustimmungskarte vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Diese Methode wird aufgerufen, wenn eine Aktionsaktivität der O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Diese Methode wird aufgerufen, wenn ein signIn überprüft, ob die Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `on_teams_task_module_fetch`        | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Abrufen eines Aufgabenmoduls zur Verfügung zu stellen. |
| task/submit                     | `on_teams_task_module_submit`       | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Übermittelt eines Aufgabenmoduls zur Verfügung zu stellen. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten sind für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch das Aufrufen von Aktivitäten speziell für Messagingerweiterungen. Weitere Informationen finden Sie unter ["Was sind Messagingerweiterungen".](https://aka.ms/azure-bot-what-are-messaging-extensions)

---
