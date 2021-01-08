---
title: Bot-Grundlagen
author: clearab
description: Grundlegendes zu den Grundlagen von Bots in Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 43dd351b30fdba3435d39aca43aae0f2de00ed24
ms.sourcegitcommit: d0e71ea63af2f67eba75ba283ec46cc7cdf87d75
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2020
ms.locfileid: "49731958"
---
# <a name="bot-basics"></a>Bot-Grundlagen

Dies ist eine Einführung, die auf dem Artikel aufbaut, in dem die Bots in der zentralen [bot-Framework-Dokumentation](https://aka.ms/azure-bot-service-docs) [arbeiten](https://aka.ms/how-bots-work) . Möglicherweise finden Sie diesen Artikel und die anderen Artikel im Abschnitt " *Konzepte* " hilfreich.

Der Hauptunterschied bei den für Microsoft Teams entwickelten Bots liegt in der Art und Weise, wie die Aktivitäten verarbeitet werden. Der Microsoft Teams-Aktivitäts Handler wird vom Aktivitäts Handler des bot-Frameworks abgeleitet, um alle Teams-Aktivitäten weiterzuleiten, bevor nicht-Teams-spezifische Aktivitäten verarbeitet werden können.

## <a name="teams-activity-handlers"></a>Teams-Aktivitäts Handler

Wenn ein Bot für Microsoft Teams eine Aktivität empfängt, leitet er diese an seine *Aktivitäts-Handler* weiter. Hinter den Kulissen arbeitet ein grundlegender Handler, der als *Turn-Handler* bezeichnet wird und durch den alle Aktivitäten geroutet werden. Der *Turn-Handler* Ruft den erforderlichen Aktivitäts Handler auf, um den Typ der empfangenen Aktivität zu verarbeiten. Wenn ein bot, der für Microsoft Teams entwickelt wurde, unterschiedlich ist, wird er von der Klasse abgeleitet `TeamsActivityHandler` , die von der Klasse des bot-Frameworks abgeleitet ist `ActivityHandler` .

# <a name="c"></a>[C#](#tab/csharp)

Wie bei jedem bot, der mit dem Microsoft bot-Framework erstellt wurde, wenn der bot eine Nachrichtenaktivität empfängt, sieht der Turn-Handler diese eingehende Aktivität und sendet Sie an den `OnMessageActivityAsync` Aktivitäts Handler. In Microsoft Teams bleibt diese Funktionalität gleich. Wenn der bot eine Unterhaltungs Aktualisierungsaktivität empfängt, sieht der Turn-Handler diese eingehende Aktivität und sendet Sie an den `OnConversationUpdateActivityAsync` . *Teams* -Aktivitäts Handler, der zuerst nach Teams-spezifischen Ereignissen sucht und an den Aktivitäts Handler des bot-Frameworks übergibt, wenn keine gefunden wird.

In der Teams-Aktivitäts Handlerklasse gibt es zwei primäre Teams-Aktivitäts Handler, `OnConversationUpdateActivityAsync` die alle Aktivitäten für das Unterhaltungs Update weiterleiten und `OnInvokeActivityAsync` alle Teams-Aufruf Aktivitäten weiterleitet.

Um Ihre Logik für Teams-spezifische Aktivitäts Handler zu implementieren, werden Sie diese Methoden in Ihrem bot außer Kraft setzen, wie im Abschnitt " [bot Logic](#bot-logic) " weiter unten gezeigt. Für jeden dieser Handler gibt es keine Basisimplementierung, fügen Sie also einfach die Logik hinzu, die Sie in die Außerkraftsetzung einfügen möchten.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Wie bei jedem bot, der mit dem Microsoft bot-Framework erstellt wurde, wenn der bot eine Nachrichtenaktivität empfängt, sieht der Turn-Handler diese eingehende Aktivität und sendet Sie an den `onMessage` Aktivitäts Handler. In Microsoft Teams bleibt diese Funktionalität gleich. Wenn der bot eine Unterhaltungs Aktualisierungsaktivität empfängt, sieht der Turn-Handler diese eingehende Aktivität und sendet Sie an den `dispatchConversationUpdateActivity` . *Teams* -Aktivitäts Handler, der zuerst nach Teams-spezifischen Ereignissen sucht und diesen an den Ereignishandler des bot-Frameworks übergibt, wenn keine gefunden wird.

In der Teams-Aktivitäts Handlerklasse gibt es zwei primäre Teams-Aktivitäts Handler, `dispatchConversationUpdateActivity` die alle Aktivitäten für das Unterhaltungs Update weiterleiten und `onInvokeActivity` alle Teams-Aufruf Aktivitäten weiterleitet.

Um Ihre Logik für Teams-spezifische Aktivitäts Handler zu implementieren, werden Sie diese Methoden in Ihrem bot außer Kraft setzen, wie im Abschnitt [bot Logic](#bot-logic) gezeigt. Definieren Sie für jeden dieser Handler ihre bot-Logik, und **rufen Sie dann `next()` am Ende an**. Durch `next()` den Aufruf stellen Sie sicher, dass der nächste Handler ausgeführt wird.

# <a name="python"></a>[Python](#tab/python)

Bots werden mithilfe des Microsoft bot-Frameworks erstellt, wenn diese bot eine Nachrichtenaktivität empfangen, dann erhält der Turn-Handler eine Benachrichtigung über diese eingehende Aktivität. Der Turn-Handler sendet dann die eingehende Aktivität an den `on_message_activity` Aktivitäts Handler. In Microsoft Teams bleibt diese Funktionalität gleich. Wenn der bot eine Unterhaltungs Aktualisierungsaktivität empfängt, erhält der Turn-Handler eine Benachrichtigung über diese eingehende Aktivität und sendet die eingehende Aktivität an `on_conversation_update_activity` . Der Handler für die Teams-Aktivität überprüft zunächst, ob es sich um Teams-spezifische Ereignisse handelt. Wenn keine Ereignisse gefunden werden, werden diese dann an den Aktivitäts Handler des bot-Frameworks übergeben.

In der Teams-Aktivitäts Handlerklasse gibt es zwei primäre Teams-Aktivitäts Handler `on_conversation_update_activity` und `on_invoke_activity` . `on_conversation_update_activity` leitet alle Aktivitäten für das Unterhaltungs Update weiter und `on_invoke_activity` leitet alle Teams-Aufruf Aktivitäten weiter.

Um Ihre Logik für Teams-spezifische Aktivitäts Handler zu implementieren, müssen Sie diese Methoden in Ihrem bot außer Kraft setzen, wie im Abschnitt [bot Logic](#bot-logic) dargestellt. Es gibt keine Basisimplementierung für diese Handler, daher müssen Sie die gewünschte Logik in ihrer Außerkraftsetzung hinzufügen.

---

## <a name="bot-logic"></a>Bot-Logik

Die bot-Logik verarbeitet eingehende Aktivitäten von einem oder mehreren ihrer bot-Kanäle und generiert ausgehende Aktivitäten als Reaktion.  Dies gilt immer noch für Bots, die von der Teams-Aktivitäts Handlerklasse abgeleitet wurden, die zunächst nach Teams-Aktivitäten sucht, und übergibt dann alle anderen Aktivitäten an den bot-Frameworks-Aktivitäts Handler.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Zentrale bot-Framework-Handler

Alle unten beschriebenen Aktivitäts Handler funktionieren weiterhin wie bei einem nicht-Teams-bot, mit Ausnahme der Aktivitäten "Mitglieder *hinzugefügt* " und " *entfernte* Mitglieder" werden diese im Kontext eines Teams unterschiedlich sein, wobei das neue Mitglied dem Team im Gegensatz zu einem Nachrichtenthread hinzugefügt wird.

Die in definierten Handler `ActivityHandler` werden unten beschrieben:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Alle empfangenen Aktivitätstypen | `OnTurnAsync` | Ruft einen der anderen Handler basierend auf dem Typ der empfangenen Aktivität auf. |
| Empfangene Nachrichtenaktivität | `OnMessageActivityAsync` | Überschreiben Sie diese, um eine Aktivität zu verarbeiten `Message` . |
| Empfangene Unterhaltungs Update Aktivität | `OnConversationUpdateActivityAsync` | Bei einer `ConversationUpdate` Aktivität wird ein Handler aufgerufen, wenn andere Mitglieder als der bot der Unterhaltung beigetreten sind oder diese verließen. |
| Nicht-bot-Mitglieder sind der Unterhaltung beigetreten | `OnMembersAddedAsync` | Überschreiben Sie diese, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Überschreiben Sie diese, um Mitglieder zu behandeln, die eine Unterhaltung hinterlassen. |
| Empfangene Ereignisaktivität | `OnEventActivityAsync` | Ruft für eine `Event` Aktivität einen für den Ereignistyp spezifischen Handler auf. |
| Empfangene Token-Response-Ereignisaktivität | `OnTokenResponseEventAsync` | Überschreiben Sie diese, um Token-Antwortereignisse zu behandeln. |
| Nicht-Token-Response-Ereignisaktivität empfangen | `OnEventAsync` | Überschreiben Sie dies, um andere Arten von Ereignissen zu behandeln. |
| Empfangene andere Aktivitätstypen | `OnUnrecognizedActivityTypeAsync` | Überschreiben Sie diese, um alle anderweitig unbehandelten Aktivitätstypen zu verarbeiten. |

#### <a name="teams-specific-handlers"></a>Teams-spezifische Handler

Die `TeamsActivityHandler` Liste der Handler oben wird erweitert, um Folgendes einzuschließen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Überschreiben Sie diesen, um einen Teams-Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) . |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Überschreiben Sie diesen, um einen Microsoft Teams-Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) .|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Überschreiben Sie diesen, um einen umbenannten Microsoft Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenannt in Channel](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) .|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Überschreiben Sie dies, um ein Teams-Team zu behandeln, das umbenannt wird. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenanntes Team](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) .|
| MembersAdded | `OnTeamsMembersAddedAsync` | Ruft die `OnMembersAddedAsync` -Methode in auf `ActivityHandler` . Überschreiben Sie diese, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügte Team Mitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) .|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Ruft die `OnMembersRemovedAsync` -Methode in auf `ActivityHandler` . Überschreiben Sie diese, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [entfernte Team Mitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) .|

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Im folgenden finden Sie eine Liste aller von dem Microsoft `OnInvokeActivityAsync` _Teams_ -Aktivitäts Handler aufgerufenen Teams-Aktivitäts Handler:

| Invoke-Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| Karten Aufruf               | `OnTeamsCardActionInvokeAsync`       | Aktionsaufruf für Teams-Karten. |
| fileeinwilligung/Invoke              | `OnTeamsFileConsentAcceptAsync`      | Zustimmung der Teams-Datei akzeptieren. |
| fileeinwilligung/Invoke              | `OnTeamsFileConsentAsync`            | Zustimmung der Teams-Datei. |
| fileeinwilligung/Invoke              | `OnTeamsFileConsentDeclineAsync`     | Zustimmung der Teams-Datei. |
| actionableMessage/Execute-Befehl | `OnTeamsO365ConnectorCardActionAsync` | Teams O365-Verbindungskarten Aktion. |
| SignIn/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Teams melden Sie sich im Verify-Zustand an. |
| Aufgabe/Abruf                      | `OnTeamsTaskModuleFetchAsync`        | Aufgabenmodul FETCH für Teams. |
| Aufgabe/Absenden                     | `OnTeamsTaskModuleSubmitAsync`       | Aufgabenmodul "Teams" übermitteln. |

Die oben aufgeführten Invoke-Aktivitäten gelten für Unterhaltungs Bots in Microsoft Teams. Das bot-Framework-SDK unterstützt auch Aufrufe speziell für Messaging-Erweiterungen. Weitere Informationen finden Sie unter [What are Messaging Extensions](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Alle nachfolgend beschriebenen Aktivitäts Handler funktionieren weiterhin wie bei einem nicht-Teams-bot, mit Ausnahme der Behandlung der Aktivitäten "Mitglieder *hinzugefügt* " und " *entfernte* Mitglieder" werden diese im Kontext eines Teams unterschiedlich sein, wobei das neue Mitglied dem Team im Gegensatz zu einem Nachrichtenthread hinzugefügt wird.

#### <a name="core-bot-framework-handlers"></a>Zentrale bot-Framework-Handler

Die in definierten Handler `ActivityHandler` werden unten beschrieben.

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Alle empfangenen Aktivitätstypen | `onTurn` | Ruft einen der anderen Handler basierend auf dem Typ der empfangenen Aktivität auf. |
| Empfangene Nachrichtenaktivität | `onMessage` | Stellen Sie eine Funktion dafür bereit, um eine Aktivität zu verarbeiten `Message` . |
| Empfangene Unterhaltungs Update Aktivität | `onConversationUpdate` | Bei einer `ConversationUpdate` Aktivität wird ein Handler aufgerufen, wenn andere Mitglieder als der bot der Unterhaltung beigetreten sind oder diese verließen. |
| Nicht-bot-Mitglieder sind der Unterhaltung beigetreten | `onMembersAdded` | Stellen Sie eine Funktion dazu bereit, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Stellen Sie eine Funktion dafür bereit, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `onEvent` | Ruft für eine `Event` Aktivität einen für den Ereignistyp spezifischen Handler auf. |
| Empfangene Token-Response-Ereignisaktivität | `onTokenResponseEvent` | Stellen Sie eine Funktion zum Behandeln von Token-Antwort Ereignissen bereit. |
| Empfangene andere Aktivitätstypen | `onUnrecognizedActivityType` | Stellen Sie eine Funktion dafür bereit, um alle anderweitig unbehandelten Aktivitätstypen zu verarbeiten. |
| Aktivitäts Handler sind abgeschlossen | `onDialog` | Stellen Sie eine Funktion dafür bereit, um jede Verarbeitung zu verarbeiten, die am Ende eines Zuges ausgeführt werden sollte, nachdem die restlichen Aktivitäts Handler abgeschlossen sind. |

#### <a name="teams-specific-handlers"></a>Teams-spezifische Handler

Die `TeamsActivityHandler` Liste der Handler im Abschnitt Core bot Framework Handler wird erweitert, um Folgendes einzuschließen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Überschreiben Sie diesen, um einen Teams-Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) . |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Überschreiben Sie diesen, um einen Microsoft Teams-Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) .|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Überschreiben Sie diesen, um einen umbenannten Microsoft Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenannt in Channel](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) . |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Überschreiben Sie dies, um ein Teams-Team zu behandeln, das umbenannt wird. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenanntes Team](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) . |
| MembersAdded | `OnTeamsMembersAddedAsync` | Ruft die `OnMembersAddedAsync` -Methode in auf `ActivityHandler` . Überschreiben Sie diese, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügte Team Mitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) . |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Ruft die `OnMembersRemovedAsync` -Methode in auf `ActivityHandler` . Überschreiben Sie diese, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [entfernte Team Mitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) . |

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Im folgenden finden Sie eine Liste aller von dem Microsoft Teams-Aktivitäts Handler aufgerufenen Teams-Aktivitäts Handler `onInvokeActivity` :

| Invoke-Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| Karten Aufruf               | `handleTeamsCardActionInvoke`       | Aktionsaufruf für Teams-Karten. |
| fileeinwilligung/Invoke              | `handleTeamsFileConsentAccept`      | Zustimmung der Teams-Datei akzeptieren. |
| fileeinwilligung/Invoke              | `handleTeamsFileConsent`            | Zustimmung der Teams-Datei. |
| fileeinwilligung/Invoke              | `handleTeamsFileConsentDecline`     | Zustimmung der Teams-Datei. |
| actionableMessage/Execute-Befehl | `handleTeamsO365ConnectorCardAction` | Teams O365-Verbindungskarten Aktion. |
| SignIn/verifyState              | `handleTeamsSigninVerifyState`      | Teams melden Sie sich im Verify-Zustand an. |
| Aufgabe/Abruf                      | `handleTeamsTaskModuleFetch`        | Aufgabenmodul FETCH für Teams. |
| Aufgabe/Absenden                     | `handleTeamsTaskModuleSubmit`       | Aufgabenmodul "Teams" übermitteln. |

Die im Abschnitt Teams Invoke Activities aufgeführten Invoke-Aktivitäten gelten für Unterhaltungs Bots in Microsoft Teams. Das bot-Framework-SDK unterstützt auch Invoke-Aktivitäten speziell für Messaging-Erweiterungen. Weitere Informationen finden Sie unter [What are Messaging Extensions](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Zentrale bot-Framework-Handler

>[!NOTE]
> Mit Ausnahme der Aktivitäten von hinzugefügten und entfernten Mitgliedern funktionieren alle in diesem Abschnitt beschriebenen Aktivitäts Handler weiterhin wie bei einem nicht-Teams-bot.

Aktivitäts Handler unterscheiden sich im Kontext eines Teams, wobei das neue Mitglied dem Team anstelle eines Nachrichten Threads hinzugefügt wird.

Die Liste der Handler `ActivityHandler` , die in definiert sind, umfasst Folgendes:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Alle empfangenen Aktivitätstypen | `on_turn` | Ruft einen der anderen Handler basierend auf dem Typ der empfangenen Aktivität auf. |
| Empfangene Nachrichtenaktivität | `on_message_activity` | Überschreibt dies, um eine Aktivität zu verarbeiten `Message` . |
| Empfangene Unterhaltungs Update Aktivität | `on_conversation_update_activity` | Ruft einen Handler auf, wenn andere Mitglieder als der bot beitreten oder die Unterhaltung verlassen. |
| Nicht-bot-Mitglieder sind der Unterhaltung beigetreten | `on_members_added_activity` | Überschreibt dies, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-bot-Mitglieder haben die Unterhaltung verlassen | `on_members_removed_activity` | Überschreibt dies zur Behandlung von Mitgliedern, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `on_event_activity` | Ruft einen Handler speziell für den Typ des Ereignisses auf. |
| Empfangene Token-Response-Ereignisaktivität | `on_token_response_event` | Überschreibt dies, um Token-Antwortereignisse zu behandeln. |
| Nicht-Token-Response-Ereignisaktivität empfangen | `on_event` | Überschreibt dies, um andere Arten von Ereignissen zu behandeln. |
| Empfangene andere Aktivitätstypen | `on_unrecognized_activity_type` | Überschreibt dies, um jede Art von Aktivität zu verarbeiten, die nicht behandelt wird. |

#### <a name="teams-specific-handlers"></a>Teams-spezifische Handler

Das `TeamsActivityHandler` erweitert die Liste der Handler aus dem Abschnitt Core Robot Framework Handlers, um Folgendes einzuschließen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Überschreibt dies, um einen Teams-Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) . |
| channelDeleted | `on_teams_channel_deleted` | Überschreibt dies, um einen Microsoft Teams-Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) .|
| channelRenamed | `on_teams_channel_renamed` | Überschreibt dies, um einen umbenannten Microsoft Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenannt in Channel](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) .|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Überschreibt dies, um ein Microsoft Teams-Team zu behandeln, das umbenannt wird. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenanntes Team](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) .|
| MembersAdded | `on_teams_members_added` | Ruft die `OnMembersAddedAsync` -Methode in auf `ActivityHandler` . Überschreibt dies zur Behandlung von Mitgliedern, die einem Team beitreten. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügte Team Mitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) .|
| MembersRemoved | `on_teams_members_removed` | Ruft die `OnMembersRemovedAsync` -Methode in auf `ActivityHandler` . Überschreibt dies zur Behandlung von Mitgliedern, die ein Team verlassen. Weitere Informationen finden Sie unter in [Unterhaltungs Update Ereignissen](https://aka.ms/azure-bot-subscribe-to-conversation-events) [entfernte Team Mitglieder](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) .|

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Die Liste der vom Team-Aktivitäts Handler aufgerufenen Teams-Aktivitäts Handler `on_invoke_activity` umfasst Folgendes:

| Invoke-Typen                    | Handler                              | Beschreibung                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| Karten Aufruf               | `on_teams_card_action_invoke`       | Aktionsaufruf für Teams-Karten. |
| fileeinwilligung/Invoke              | `on_teams_file_consent_accept`      | Zustimmung der Teams-Datei akzeptieren. |
| fileeinwilligung/Invoke              | `on_teams_file_consent`            | Zustimmung der Teams-Datei. |
| fileeinwilligung/Invoke              | `on_teams_file_consent_decline`     | Ablehnung von Teams-Datei Zustimmung. |
| actionableMessage/Execute-Befehl | `on_teams_o365_connector_card_action` | Teams O365-Verbindungskarten Aktion. |
| SignIn/verifyState              | `on_teams_signin_verify_state`      | Teams melden Sie sich im Verify-Zustand an. |
| Aufgabe/Abruf                      | `on_teams_task_module_fetch`        | Aufgabenmodul FETCH für Teams. |
| Aufgabe/Absenden                     | `on_teams_task_module_submit`       | Aufgabenmodul "Teams" übermitteln. |

Die im Abschnitt Teams Invoke Activities aufgeführten Invoke-Aktivitäten gelten für Unterhaltungs Bots in Microsoft Teams. Das bot-Framework-SDK unterstützt auch Invoke-Aktivitäten speziell für Messaging-Erweiterungen. Weitere Informationen finden Sie unter [What are Messaging Extensions](https://aka.ms/azure-bot-what-are-messaging-extensions).

---
