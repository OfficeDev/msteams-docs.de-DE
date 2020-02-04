---
title: Bot-Grundlagen
author: clearab
description: Grundlegendes zu den Grundlagen von Bots in Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: e1b0c79b73ae89c8ab76ba0a1ff045603ab0b932
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674247"
---
# <a name="bot-basics"></a>Bot-Grundlagen

Dies ist eine Einführung, die auf dem Artikel aufbaut, in dem die Bots in der zentralen [bot-Framework-Dokumentation](https://aka.ms/azure-bot-service-docs) [arbeiten](https://aka.ms/how-bots-work) . Möglicherweise finden Sie diesen Artikel und die anderen Artikel im Abschnitt " *Konzepte* " hilfreich.

Der Hauptunterschied bei den für Microsoft Teams entwickelten Bots liegt in der Art und Weise, wie Aktivitäten behandelt werden. Der Microsoft Teams-Aktivitäts Handler wird vom Aktivitäts Handler des bot-Frameworks abgeleitet, um alle Teams-Aktivitäten weiterzuleiten, bevor nicht-Teams-spezifische Aktivitäten verarbeitet werden können.

## <a name="teams-activity-handlers"></a>Teams-Aktivitäts Handler

Wenn ein bot für Microsoft Teams eine Aktivität empfängt, übergibt er ihn an seine *Aktivitäts Handler*. Unter dem Cover gibt es einen Basis Handler namens *Turn Handler*, über den alle Aktivitäten weitergeleitet werden. Der *Turn-Handler* Ruft den erforderlichen Aktivitäts Handler auf, um den Typ der empfangenen Aktivität zu verarbeiten. Wenn ein bot, der für Microsoft Teams entwickelt wurde, unterschiedlich `TeamsActivityHandler` ist, wird er von der Klasse abgeleitet, `ActivityHandler` die von der Klasse des bot-Frameworks abgeleitet ist.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Wie bei jedem bot, der mit dem Microsoft bot-Framework erstellt wurde, wenn der bot eine Nachrichtenaktivität empfängt, sieht der Turn-Handler diese eingehende `OnMessageActivityAsync` Aktivität und sendet Sie an den Aktivitäts Handler. In Microsoft Teams bleibt diese Funktionalität gleich. Wenn der bot eine Unterhaltungs Aktualisierungsaktivität empfängt, sieht der Turn-Handler diese eingehende Aktivität und sendet Sie `OnConversationUpdateActivityAsync` an den *Teams* -Aktivitäts Handler, der zuerst nach Teams-spezifischen Ereignissen sucht und Sie an den Aktivitäts Handler des bot-Frameworks übergibt, wenn keine gefunden wird.

In der Teams-Aktivitäts Handlerklasse gibt es zwei primäre Teams-Aktivitäts Handler, `OnConversationUpdateActivityAsync` die alle Aktivitäten für das Unterhaltungs Update weiter `OnInvokeActivityAsync` leiten und alle Teams-Aufruf Aktivitäten weiterleitet.

Um Ihre Logik für Teams-spezifische Aktivitäts Handler zu implementieren, werden Sie diese Methoden in Ihrem bot außer Kraft setzen, wie im Abschnitt " [bot Logic](#bot-logic) " weiter unten gezeigt. Für jeden dieser Handler gibt es keine Basisimplementierung, fügen Sie also einfach die Logik hinzu, die Sie in die Außerkraftsetzung einfügen möchten.

# <a name="javascripttabjavascript"></a>[JavaScript](#tab/javascript)

Wie bei jedem bot, der mit dem Microsoft bot-Framework erstellt wurde, wenn der bot eine Nachrichtenaktivität empfängt, sieht der Turn-Handler diese eingehende `onMessage` Aktivität und sendet Sie an den Aktivitäts Handler. In Microsoft Teams bleibt diese Funktionalität gleich. Wenn der bot eine Unterhaltungs Update Aktivität empfängt, sieht der Turn-Handler diese eingehende Aktivität und sendet Sie `dispatchConversationUpdateActivity` an den *Teams* -Aktivitäts Handler, der zuerst nach Teams-spezifischen Ereignissen sucht und Sie an den bot-Frameworks-Aktivitäts Handler übergibt, wenn keine gefunden wird.

In der Teams-Aktivitäts Handlerklasse gibt es zwei primäre Teams-Aktivitäts Handler, `dispatchConversationUpdateActivity` die alle Aktivitäten für das Unterhaltungs Update weiter `onInvokeActivity` leiten und alle Teams-Aufruf Aktivitäten weiterleitet.

Um Ihre Logik für Teams-spezifische Aktivitäts Handler zu implementieren, werden Sie diese Methoden in Ihrem bot außer Kraft setzen, wie im Abschnitt " [bot Logic](#bot-logic) " weiter unten gezeigt. Definieren Sie für jeden dieser Handler ihre bot-Logik, und **rufen `next()` Sie dann am Ende an**. Durch den `next()` Aufruf stellen Sie sicher, dass der nächste Handler ausgeführt wird.

---

## <a name="bot-logic"></a>Bot-Logik

Die bot-Logik verarbeitet eingehende Aktivitäten von einem oder mehreren ihrer bot-Kanäle und generiert ausgehende Aktivitäten als Reaktion.  Dies gilt immer noch für Bots, die von der Teams-Aktivitäts Handlerklasse abgeleitet wurden, die zunächst nach Teams-Aktivitäten sucht, und übergibt dann alle anderen Aktivitäten an den bot-Frameworks-Aktivitäts Handler.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Zentrale bot-Framework-Handler

Alle unten beschriebenen Aktivitäts Handler funktionieren weiterhin wie bei einem nicht-Teams-bot, mit Ausnahme der Aktivitäten "Mitglieder *hinzugefügt* " und " *entfernte* Mitglieder" werden diese im Kontext eines Teams unterschiedlich sein, wobei das neue Mitglied dem Team im Gegensatz zu einem Nachrichtenthread hinzugefügt wird.

Die in `ActivityHandler` definierten Handler werden unten beschrieben.

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Alle empfangenen Aktivitätstypen | `OnTurnAsync` | Ruft einen der anderen Handler basierend auf dem Typ der empfangenen Aktivität auf. |
| Empfangene Nachrichtenaktivität | `OnMessageActivityAsync` | Überschreiben Sie diese, `Message` um eine Aktivität zu verarbeiten. |
| Empfangene Unterhaltungs Update Aktivität | `OnConversationUpdateActivityAsync` | Bei einer `ConversationUpdate` Aktivität wird ein Handler aufgerufen, wenn andere Mitglieder als der bot der Unterhaltung beigetreten sind oder diese verließen. |
| Nicht-bot-Mitglieder sind der Unterhaltung beigetreten | `OnMembersAddedAsync` | Überschreiben Sie diese, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-bot-Mitglieder haben die Unterhaltung verlassen | `OnMembersRemovedAsync` | Überschreiben Sie diese, um Mitglieder zu behandeln, die eine Unterhaltung hinterlassen. |
| Empfangene Ereignisaktivität | `OnEventActivityAsync` | Ruft für `Event` eine Aktivität einen für den Ereignistyp spezifischen Handler auf. |
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
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Überschreiben Sie dies, um ein Teams-Team zu behandeln, das umbenannt wird. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenanntes Team](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) .|
| MembersAdded | `OnTeamsMembersAddedAsync` | Ruft die `OnMembersAddedAsync` -Methode `ActivityHandler`in auf. Überschreiben Sie diese, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügtes Team Mitglied](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Added) .|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Ruft die `OnMembersRemovedAsync` -Methode `ActivityHandler`in auf. Überschreiben Sie diese, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [entferntes Team Mitglied](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Removed) .|

#### <a name="teams-invoke--activities"></a>Teams rufen Aktivitäten auf

Im folgenden finden Sie eine Liste aller von dem `OnInvokeActivityAsync` Microsoft _Teams_ -Aktivitäts Handler aufgerufenen Teams-Aktivitäts Handler:

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

# <a name="javascripttabjavascript"></a>[JavaScript](#tab/javascript)

Alle nachfolgend beschriebenen Aktivitäts Handler funktionieren weiterhin wie bei einem nicht-Teams-bot, mit Ausnahme der Behandlung der Aktivitäten "Mitglieder *hinzugefügt* " und " *entfernte* Mitglieder" werden diese im Kontext eines Teams unterschiedlich sein, wobei das neue Mitglied dem Team im Gegensatz zu einem Nachrichtenthread hinzugefügt wird.

#### <a name="core-bot-framework-handlers"></a>Zentrale bot-Framework-Handler

Die in `ActivityHandler` definierten Handler werden unten beschrieben.

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| Alle empfangenen Aktivitätstypen | `onTurn` | Ruft einen der anderen Handler basierend auf dem Typ der empfangenen Aktivität auf. |
| Empfangene Nachrichtenaktivität | `onMessage` | Stellen Sie eine Funktion dafür bereit, um `Message` eine Aktivität zu verarbeiten. |
| Empfangene Unterhaltungs Update Aktivität | `onConversationUpdate` | Bei einer `ConversationUpdate` Aktivität wird ein Handler aufgerufen, wenn andere Mitglieder als der bot der Unterhaltung beigetreten sind oder diese verließen. |
| Nicht-bot-Mitglieder sind der Unterhaltung beigetreten | `onMembersAdded` | Stellen Sie eine Funktion dazu bereit, um Mitglieder zu behandeln, die einer Unterhaltung beitreten. |
| Nicht-bot-Mitglieder haben die Unterhaltung verlassen | `onMembersRemoved` | Stellen Sie eine Funktion dafür bereit, um Mitglieder zu behandeln, die eine Unterhaltung verlassen. |
| Empfangene Ereignisaktivität | `onEvent` | Ruft für `Event` eine Aktivität einen für den Ereignistyp spezifischen Handler auf. |
| Empfangene Token-Response-Ereignisaktivität | `onTokenResponseEvent` | Stellen Sie eine Funktion zum Behandeln von Token-Antwort Ereignissen bereit. |
| Empfangene andere Aktivitätstypen | `onUnrecognizedActivityType` | Stellen Sie eine Funktion dafür bereit, um alle anderweitig unbehandelten Aktivitätstypen zu verarbeiten. |
| Aktivitäts Handler sind abgeschlossen | `onDialog` | Stellen Sie eine Funktion dafür bereit, um jede Verarbeitung zu verarbeiten, die am Ende eines Zuges ausgeführt werden sollte, nachdem die restlichen Aktivitäts Handler abgeschlossen sind. |

#### <a name="teams-specific-handlers"></a>Teams-spezifische Handler

Die `TeamsActivityHandler` Liste der Handler oben wird erweitert, um Folgendes einzuschließen:

| Ereignis | Handler | Beschreibung |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Überschreiben Sie diesen, um einen Teams-Kanal zu verarbeiten, der erstellt wird. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [erstellter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) . |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Überschreiben Sie diesen, um einen Microsoft Teams-Kanal zu verarbeiten, der gelöscht wird. Weitere Informationen finden Sie unter unter [Haltungs Update-Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [gelöschter Kanal](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) .|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Überschreiben Sie diesen, um einen umbenannten Microsoft Teams-Kanal zu verarbeiten. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenannt in Channel](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) . |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Überschreiben Sie dies, um ein Teams-Team zu behandeln, das umbenannt wird. Weitere Informationen finden Sie unter [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events) [umbenanntes Team](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) . |
| MembersAdded | `OnTeamsMembersAddedAsync` | Ruft die `OnMembersAddedAsync` -Methode `ActivityHandler`in auf. Überschreiben Sie diese, um Mitglieder zu behandeln, die einem Team beitreten. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [hinzugefügtes Team Mitglied](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Added) . |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Ruft die `OnMembersRemovedAsync` -Methode `ActivityHandler`in auf. Überschreiben Sie diese, um Mitglieder zu behandeln, die ein Team verlassen. Weitere Informationen finden Sie unter [Unterhaltungs Update Ereignisse](https://aka.ms/azure-bot-subscribe-to-conversation-events) [entferntes Team Mitglied](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Removed) . |

#### <a name="teams-invoke-activities"></a>Teams rufen Aktivitäten auf

Im folgenden finden Sie eine Liste aller von dem `onInvokeActivity` Microsoft _Teams_ -Aktivitäts Handler aufgerufenen Teams-Aktivitäts Handler:

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

Die oben aufgeführten Invoke-Aktivitäten gelten für Unterhaltungs Bots in Microsoft Teams. Das bot-Framework-SDK unterstützt auch für Messaging-Erweiterungen spezifische Aufrufe. Weitere Informationen finden Sie unter [What are Messaging Extensions](https://aka.ms/azure-bot-what-are-messaging-extensions)

---
