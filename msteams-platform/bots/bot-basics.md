---
title: Bot-Aktivitätenhandler
author: clearab
description: Verstehen der Botaktivitätshandler in Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 22f4c3f3addcf87b3fb34a1b7b3d40d2092b8a44
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696430"
---
# <a name="bot-activity-handlers"></a>Bot-Aktivitätenhandler

Dieses Dokument baut auf dem Artikel zur Funktionsweise von [Bots](https://aka.ms/how-bots-work) in der grundlegenden [Bot Framework-Dokumentation auf.](https://aka.ms/azure-bot-service-docs) Der Hauptunterschied zwischen Bots, die für Microsoft Teams entwickelt wurden, und dem Kern von Bot Framework liegt in den in Teams bereitgestellten Features.

Zum Organisieren der Unterhaltungslogik für Ihren Bot wird ein Aktivitätshandler verwendet. Aktivitäten werden auf zwei Arten mithilfe von Teams-Aktivitätshandlern und Botlogik behandelt. Der Microsoft Teams-Aktivitätshandler bietet Unterstützung für Microsoft Teams-spezifische Ereignisse und Interaktionen. Das Bot-Objekt enthält die Unterhaltungsgrundhaltung oder Logik für eine Drehung und macht einen Turn-Handler verfügbar, die Methode, die eingehende Aktivitäten vom Botadapter akzeptieren kann.

## <a name="teams-activity-handlers"></a>Teams-Aktivitätshandler

Der Aktivitätshandler von Teams wird vom Aktivitätshandler von Microsoft Bot Framework abgeleitet. Es leitet alle Teams-Aktivitäten weiter, bevor nicht teamsspezifische Aktivitäten behandelt werden können.

Wenn ein Bot für Teams eine Aktivität empfängt, wird er an die Aktivitätshandler geroutet. Alle Aktivitäten werden über einen Basishandler, den turn handler, geroutet. Der Turnhandler ruft den erforderlichen Aktivitätshandler auf, um alle empfangenen Aktivitäten zu verwalten. Der Teams-Bot wird von der Klasse abgeleitet, die von der `TeamsActivityHandler` Bot Framework-Klasse abgeleitet `ActivityHandler` ist.

# <a name="c"></a>[C#](#tab/csharp)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität empfangen, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `OnMessageActivityAsync` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `OnConversationUpdateActivityAsync` . Der Teams-Aktivitätshandler überprüft zunächst auf bestimmte Teams-Ereignisse. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot Frameworks übergeben.

In der Teams-Aktivitätshandlerklasse gibt es zwei primäre Teams-Aktivitätshandler `OnConversationUpdateActivityAsync` und `OnInvokeActivityAsync` . `OnConversationUpdateActivityAsync` leitet alle Unterhaltungsaktualisierungsaktivitäten und `OnInvokeActivityAsync` leitet alle Von Teams aufgerufenen Aktivitäten fort.

Um Ihre Logik für bestimmte Aktivitätshandler von Teams zu implementieren, müssen Sie die Methoden in Ihrem Bot außer Kraft setzen, wie im Abschnitt [Botlogik](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler, daher müssen Sie die logik hinzufügen, die Sie in Der Außerkraftsetzung wünschen.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität empfangen, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `onMessage` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `dispatchConversationUpdateActivity` . Der Teams-Aktivitätshandler überprüft zunächst auf bestimmte Teams-Ereignisse. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot Frameworks übergeben.

In der Teams-Aktivitätshandlerklasse gibt es zwei primäre Teams-Aktivitätshandler `dispatchConversationUpdateActivity` und `onInvokeActivity` . `dispatchConversationUpdateActivity` leitet alle Unterhaltungsaktualisierungsaktivitäten und `onInvokeActivity` leitet alle Von Teams aufgerufenen Aktivitäten fort.

Um Ihre Logik für bestimmte Aktivitätshandler von Teams zu implementieren, müssen Sie die Methoden in Ihrem Bot außer Kraft setzen, wie im Abschnitt [Botlogik](#bot-logic) gezeigt. Definieren Sie Ihre Botlogik für diese Handler, und rufen Sie am Ende `next()` unbedingt auf. Durch aufrufen `next()` stellen Sie sicher, dass der nächste Handler ausgeführt wird.

# <a name="python"></a>[Python](#tab/python)

Bots werden mit dem Bot Framework erstellt. Wenn die Bots eine Nachrichtenaktivität empfangen, erhält der Turnhandler eine Benachrichtigung über diese eingehende Aktivität. Der Turnhandler sendet dann die eingehende Aktivität an den `on_message_activity` Aktivitätshandler. In Teams bleibt diese Funktionalität unverändert. Wenn der Bot eine Unterhaltungsaktualisierungsaktivität empfängt, empfängt der Turnhandler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `on_conversation_update_activity` . Der Teams-Aktivitätshandler überprüft zunächst auf bestimmte Teams-Ereignisse. Wenn keine Ereignisse gefunden werden, werden sie an den Aktivitätshandler des Bot Frameworks übergeben.

In der Teams-Aktivitätshandlerklasse gibt es zwei primäre Teams-Aktivitätshandler `on_conversation_update_activity` und `on_invoke_activity` . `on_conversation_update_activity` leitet alle Unterhaltungsaktualisierungsaktivitäten und `on_invoke_activity` leitet alle Von Teams aufgerufenen Aktivitäten fort.

Um Ihre Logik für bestimmte Aktivitätshandler von Teams zu implementieren, müssen Sie die Methoden in Ihrem Bot außer Kraft setzen, wie im Abschnitt [Botlogik](#bot-logic) gezeigt. Es gibt keine Basisimplementierung für diese Handler, daher müssen Sie die logik hinzufügen, die Sie in Der Außerkraftsetzung wünschen.

---

## <a name="bot-logic"></a>Bot-Logik

Die Botlogik verarbeitet eingehende Aktivitäten von einem oder mehreren Botkanälen und generiert als Reaktion ausgehende Aktivitäten. Dies gilt weiterhin für Bots, die von der Teams-Aktivitätshandlerklasse abgeleitet wurden, die zunächst auf Teams-Aktivitäten überprüft. Nach der Überprüfung auf Teams-Aktivitäten werden alle anderen Aktivitäten an den Aktivitätshandler des Bot Frameworks übergeben.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework Handler

>[!NOTE]
> Mit Ausnahme der  Aktivitäten **hinzugefügter** und entfernter Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem dem Team anstelle eines Nachrichtenthreads ein neues Mitglied hinzugefügt wird.

Die Liste der in definierten Handler `ActivityHandler` umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `OnTurnAsync` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Empfangene Nachrichtenaktivität | `OnMessageActivityAsync` | Diese Methode kann überschrieben werden, um eine Aktivität zu `Message` verarbeiten. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `OnConversationUpdateActivityAsync` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer Aktivität beigetreten sind oder diese verlassen `ConversationUpdate` haben. |
| Nicht-Bot-Mitglieder haben der Unterhaltung beigetreten | `OnMembersAddedAsync` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Diese Methode kann überschrieben werden, um Elemente zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `OnEventActivityAsync` | Diese Methode ruft einen Handler auf, der für den Ereignistyp spezifisch ist, für eine `Event` Aktivität. |
| Empfangene Tokenantwortereignisaktivität | `OnTokenResponseEventAsync` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Ereignisaktivität ohne Tokenantwort | `OnEventAsync` | Diese Methode kann überschrieben werden, um andere Ereignistypen zu behandeln. |
| Anderer Aktivitätstyp empfangen | `OnUnrecognizedActivityTypeAsync` | Diese Methode kann außer Kraft gesetzt werden, um einen beliebigen Aktivitätstyp zu verarbeiten, der andernfalls nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätshandler

Der `TeamsActivityHandler` erweitert die Liste der Handler im Hauptabschnitt Bot Framework-Handler, um Folgendes zu umfassen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen zu erstellenden Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Kanal, der](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) in [Unterhaltungsaktualisierungsereignissen erstellt wurde.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen zu löschenden Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) gelöscht in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen umbenannten Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter [Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsupdateereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Diese Methode kann überschrieben werden, um ein umbenanntes Teams-Team zu behandeln. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in conversation [update events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie [unter Teammitglieder, die](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) in Unterhaltungsaktualisierungsereignissen [hinzugefügt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie [unter Teammitglieder, die](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) in Unterhaltungsaktualisierungsereignissen [entfernt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|

#### <a name="teams-invoke-activities"></a>Teams ruft Aktivitäten auf

Die Liste der Teams-Aktivitätshandler, die vom `OnInvokeActivityAsync` Teams-Aktivitätshandler aufgerufen werden, umfasst Folgendes:

| Aufrufen von Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Diese Methode wird aufgerufen, wenn eine Aktion einer O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Diese Methode wird aufgerufen, wenn ein signIn überprüft, ob Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Abrufen eines Aufgabenmoduls zur Verfügung zu stellen. |
| task/submit                     | `OnTeamsTaskModuleSubmitAsync`       | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Übermittelt eines Aufgabenmoduls zu liefern. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten sind für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch das Aufrufen von Aktivitäten speziell für Messagingerweiterungen. Weitere Informationen finden Sie unter [Was sind Messagingerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework Handler

>[!NOTE]
> Mit Ausnahme der  Aktivitäten **hinzugefügter** und entfernter Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der in definierten Handler `ActivityHandler` umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `onTurn` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Empfangene Nachrichtenaktivität | `onMessage` | Diese Methode hilft beim Behandeln einer `Message` Aktivität. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `onConversationUpdate` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung bei einer Aktivität beigetreten sind oder diese verlassen `ConversationUpdate` haben. |
| Nicht-Bot-Mitglieder haben der Unterhaltung beigetreten | `onMembersAdded` | Diese Methode hilft, Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Diese Methode hilft bei der Behandlung von Mitgliedern, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `onEvent` | Diese Methode ruft einen Handler auf, der für den Ereignistyp spezifisch ist, für eine `Event` Aktivität. |
| Empfangene Tokenantwortereignisaktivität | `onTokenResponseEvent` | Diese Methode hilft beim Behandeln von Tokenantwortereignissen. |
| Anderer Aktivitätstyp empfangen | `onUnrecognizedActivityType` | Diese Methode hilft bei der Behandlung eines beliebigen Aktivitätstyps, der andernfalls nicht behandelt wird. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätshandler

Der `TeamsActivityHandler` erweitert die Liste der Handler im Hauptabschnitt Bot Framework-Handler, um Folgendes zu umfassen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Diese Methode kann überschrieben werden, um einen zu erstellenden Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Kanal, der](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) in [Unterhaltungsaktualisierungsereignissen erstellt wurde.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Diese Methode kann überschrieben werden, um einen zu löschenden Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) gelöscht in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Diese Methode kann überschrieben werden, um einen umbenannten Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter [Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsupdateereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Diese Methode kann überschrieben werden, um ein umbenanntes Teams-Team zu behandeln. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in conversation [update events](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie [unter Teammitglieder, die](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) in Unterhaltungsaktualisierungsereignissen [hinzugefügt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie [unter Teammitglieder, die](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) in Unterhaltungsaktualisierungsereignissen [entfernt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |

#### <a name="teams-invoke-activities"></a>Teams ruft Aktivitäten auf

Die Liste der Teams-Aktivitätshandler, die vom `onInvokeActivity` Teams-Aktivitätshandler aufgerufen werden, umfasst Folgendes:

| Aufrufen von Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Diese Methode wird aufgerufen, wenn eine Aktion einer O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Diese Methode wird aufgerufen, wenn ein signIn überprüft, ob Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Abrufen eines Aufgabenmoduls zur Verfügung zu stellen. |
| task/submit                     | `handleTeamsTaskModuleSubmit`       | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Übermittelt eines Aufgabenmoduls zu liefern. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten sind für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch das Aufrufen von Aktivitäten speziell für Messagingerweiterungen. Weitere Informationen finden Sie unter [Was sind Messagingerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Core Bot Framework Handler

>[!NOTE]
> Mit Ausnahme der  Aktivitäten **hinzugefügter** und entfernter Mitglieder funktionieren alle in diesem Abschnitt beschriebenen Aktivitätshandler weiterhin wie bei einem Nicht-Teams-Bot.

Aktivitätshandler unterscheiden sich im Kontext eines Teams, in dem das neue Mitglied dem Team anstelle eines Nachrichtenthreads hinzugefügt wird.

Die Liste der in definierten Handler `ActivityHandler` umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Jeder empfangene Aktivitätstyp | `on_turn` | Diese Methode ruft einen der anderen Handler auf, basierend auf dem Typ der empfangenen Aktivität. |
| Empfangene Nachrichtenaktivität | `on_message_activity` | Diese Methode kann überschrieben werden, um eine Aktivität zu `Message` verarbeiten. |
| Empfangene Unterhaltungsaktualisierungsaktivität | `on_conversation_update_activity` | Diese Methode ruft einen Handler auf, wenn andere Mitglieder als der Bot der Unterhaltung beitreten oder diese verlassen. |
| Nicht-Bot-Mitglieder haben der Unterhaltung beigetreten | `on_members_added_activity` | Diese Methode kann überschrieben werden, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-Bot-Mitglieder haben die Unterhaltung verlassen | `on_members_removed_activity` | Diese Methode kann überschrieben werden, um Elemente zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `on_event_activity` | Diese Methode ruft einen Handler auf, der für den Ereignistyp spezifisch ist. |
| Empfangene Tokenantwortereignisaktivität | `on_token_response_event` | Diese Methode kann überschrieben werden, um Tokenantwortereignisse zu behandeln. |
| Empfangene Ereignisaktivität ohne Tokenantwort | `on_event` | Diese Methode kann überschrieben werden, um andere Ereignistypen zu behandeln. |
| Andere empfangene Aktivitätstypen | `on_unrecognized_activity_type` | Diese Methode kann überschrieben werden, um alle Arten von Aktivitäten zu behandeln, die nicht behandelt werden. |

#### <a name="teams-specific-activity-handlers"></a>Teams-spezifische Aktivitätshandler

Der erweitert die Liste der Handler aus dem `TeamsActivityHandler` Hauptabschnitt Bot Framework-Handler, um Folgendes zu umfassen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Diese Methode kann überschrieben werden, um einen zu erstellenden Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Kanal, der](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) in [Unterhaltungsaktualisierungsereignissen erstellt wurde.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `on_teams_channel_deleted` | Diese Methode kann überschrieben werden, um einen zu löschenden Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) gelöscht in [Unterhaltungsaktualisierungsereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `on_teams_channel_renamed` | Diese Methode kann überschrieben werden, um einen umbenannten Teams-Kanal zu behandeln. Weitere Informationen finden Sie unter [Kanal umbenannt](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) in [Unterhaltungsupdateereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Diese Methode kann überschrieben werden, um ein umbenanntes Teams-Team zu behandeln. Weitere Informationen finden Sie unter [team renamed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in conversation [update events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Diese Methode ruft die `OnMembersAddedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie [unter Teammitglieder, die](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) in Unterhaltungsaktualisierungsereignissen [hinzugefügt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersRemoved | `on_teams_members_removed` | Diese Methode ruft die `OnMembersRemovedAsync` Methode in `ActivityHandler` auf. Die Methode kann überschrieben werden, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie [unter Teammitglieder, die](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) in Unterhaltungsaktualisierungsereignissen [entfernt wurden.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|

#### <a name="teams-invoke-activities"></a>Teams ruft Aktivitäten auf

Die Liste der Teams-Aktivitätshandler, die vom `on_invoke_activity` Teams-Aktivitätshandler aufgerufen werden, umfasst Folgendes:

| Aufrufen von Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Diese Methode wird aufgerufen, wenn eine Aktivität zum Aufrufen einer Kartenaktion vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer akzeptiert wird. |
| fileConsent/invoke              | `on_teams_file_consent`            | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskartenaktivität vom Connector empfangen wird. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Diese Methode wird aufgerufen, wenn eine Datei-Zustimmungskarte vom Benutzer abgelehnt wird. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Diese Methode wird aufgerufen, wenn eine Aktion einer O365-Connectorkarte vom Connector empfangen wird. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Diese Methode wird aufgerufen, wenn ein signIn überprüft, ob Statusaktivität vom Connector empfangen wird. |
| task/fetch                      | `on_teams_task_module_fetch`        | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Abrufen eines Aufgabenmoduls zur Verfügung zu stellen. |
| task/submit                     | `on_teams_task_module_submit`       | Diese Methode kann in einer abgeleiteten Klasse außer Kraft gesetzt werden, um Logik beim Übermittelt eines Aufgabenmoduls zu liefern. |

Die in diesem Abschnitt aufgeführten Aufrufaktivitäten sind für Unterhaltungsbots in Teams. Das Bot Framework SDK unterstützt auch das Aufrufen von Aktivitäten speziell für Messagingerweiterungen. Weitere Informationen finden Sie unter [Was sind Messagingerweiterungen](https://aka.ms/azure-bot-what-are-messaging-extensions).

---

* * *

Nachdem Sie sich nun mit Botaktivitätshandlern vertraut machen, können wir sehen, wie sich Bots je nach Unterhaltung und den empfangenen oder gesendeten Nachrichten unterschiedlich verhalten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Grundlagen zu Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
