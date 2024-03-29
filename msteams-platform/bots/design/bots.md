---
title: Entwerfen Ihres Bots
description: In diesem Modul erfahren Sie, wie Sie einen Teams Bot und seine Anwendungsfälle entwerfen und hinzufügen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.openlocfilehash: 4571dfb49a8549ef644c392d3f05a6f2611b0f14
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66557932"
---
# <a name="designing-your-microsoft-teams-bot"></a>Entwerfen Ihres Microsoft Teams-Bots

Bots sind Unterhaltungs-Apps, die bestimmte Aufgaben ausführen. Basierend auf dem <a href="https://dev.botframework.com/" target="_blank">Microsoft Bot Framework</a> kommunizieren Bots mit Benutzern, beantworten ihre Fragen und benachrichtigen sie proaktiv über Änderungen und andere Ereignisse. Sie sind eine tolle Möglichkeit zur Kontaktaufnahme.

> [!IMPORTANT]
> Bots sind in Government Community Cloud(GCC)- und GCC High-Umgebungen, aber nicht in Department of Defense (DoD)-Umgebungen verfügbar.

Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Bots in Teams hinzufügen, verwenden und verwalten können, um Ihr App-Design zu steuern.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Richtlinien für das Bot-Design, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a>Einen Bot hinzufügen

Bots sind in Chats, Kanälen und persönlichen Apps verfügbar.

### <a name="mobile"></a>Mobilgerät

Benutzer können Bots erreichen, die dem Desktop hinzugefügt wurden, indem auf sie mit einer @mention zugegriffen wird.

:::image type="content" source="../../assets/images/bots/mobile-access-bot-chat-at-mention.png" alt-text="Beispiel zeigt, wie Sie mithilfe einer @mention auf einen mobilen Bot in einem Gruppenchat zugreifen.":::

### <a name="desktop"></a>Desktop

Benutzer können einen Bot auf eine der folgenden Arten hinzufügen:

* Aus dem Teams Store.
* Verwenden des App-Flyouts durch Auswahl des Symbols **Mehr** auf der linken Seite von Teams.
* Mit einer @Erwähnung im neuen Chat- oder Erstellungsfeld (das folgende Beispiel zeigt, wie Sie dies in einem Gruppenchat tun können).

    :::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Beispiel: So fügen Sie einen Bot in einem Gruppenchat mit einer @Erwähnung hinzu.":::

## <a name="introduce-a-bot"></a>Einführen eines Bots

Es ist wichtig, dass sich Ihr Bot vorstellt und beschreibt, was er kann. Dieser anfängliche Austausch hilft Personen zu verstehen, was sie mit dem Bot tun sollen, seine Beschränkungen herauszufinden und sich vor allem mit ihm vertraut zu machen.

### <a name="welcome-message-in-a-one-on-one-chat"></a>Willkommensnachricht in einem 1:1-Chat

In persönlichen Kontexten geben Willkommensnachrichten den Ton Ihres Bots an. Die Nachricht enthält eine Begrüßung, was der Bot tun kann und einige Vorschläge wie man interagiert. Beispiel: "Versuchen Sie, mich nach ... zu fragen“. Wenn möglich, sollten diese Vorschläge gespeicherte Antworten zurückgeben, ohne sich anmelden zu müssen.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-personal-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einer persönlichen App auf einem Mobilgerät.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einer persönlichen App.":::

### <a name="welcome-message-in-channels-and-group-chats"></a>Willkommensnachricht in Kanälen und Gruppenchats

Die Einführung Ihres Bots sollte sich in Kanälen und Gruppenchats im Vergleich zu einem persönlichen Bereich (zum Beispiel einer persönlichen App) geringfügig unterscheiden. Wenn Sie in der realen Welt einen Raum voller Personen betreten haben, würden Sie sich vorstellen, anstatt alle zu begrüßen, die bereits dort sind. Lassen Sie dieses Denken in Ihr Bot-Design einfließen.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-group-welcome.png" alt-text="Beispiel zeigt eine Boteinführung in einem gemeinschaftlichen Kontext auf einem Mobilgerät.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Beispiel zeigt eine Bot-Einführung in einem kollaborativen Kontext.":::

### <a name="bot-authentication-with-single-sign-on"></a>Bot-Authentifizierung mit Single Sign-On

Wenn eine Person einem Bot eine Nachricht sendet, muss möglicherweise eine Anmeldung erforderlich sein, um alle Funktionen zu nutzen. Sie können den Authentifizierungsprozess mithilfe von Single Sign-On (SSO) vereinfachen.

Vergessen Sie nicht: Im Bot-Befehlsmenü (**Was kann ich tun?**) müssen Sie auch einen Befehl zum Abmelden eingeben.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-sso-example.png" alt-text="Beispiel zeigt einen Bot mit einer Anmeldeschaltfläche auf einem Mobilgerät.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Beispiel zeigt einen Bot mit einer Anmeldeschaltfläche.":::

### <a name="tours"></a>Touren

Sie können eine Tour mit Begrüßungsnachrichten einfügen und wenn der Bot auf so etwas wie einen Hilfebefehl reagiert. Eine Tour ist der effektivste Weg, um zu beschreiben, was Ihr Bot tun kann. Falls zutreffend, eignen sie sich auch hervorragend zur Beschreibung der anderen Features Ihrer App. Fügen Sie beispielsweise Screenshots Ihrer Nachrichtenerweiterung ein.

> [!IMPORTANT]
> Touren sollten zugänglich sein, ohne sich anmelden zu müssen.

### <a name="one-on-one-chats"></a>1:1-Chats

In einer persönlichen App bietet ein Karussell einen effektiven Überblick über Ihren Bot und alle anderen Features Ihrer App. Das Einschließen von Schaltflächen, mit denen Benutzer Bot-Befehle ausprobieren können, wird empfohlen. Erstellen Sie z. B. **eine Aufgabe**.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-tour-personal.png" alt-text="Beispiel zeigt eine Bot-Tour in einem Zweipersonenchat auf Mobilgeräten.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Beispiel zeigt eine Bot-Tour in einem 1:1-Chat.":::

### <a name="channels-and-group-chats"></a>Kanäle und Gruppenchats

In Kanälen und Gruppenchats sollte eine Tour in einem Modal (auch als [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) bezeichnet) geöffnet werden, damit laufende Gespräche nicht unterbrochen werden. Dies gibt Ihnen auch die Möglichkeit, rollenbasierte Ansichten für Ihre Tour zu implementieren.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-tour-channel.png" alt-text="Beispiel zeigt eine Bot-Tour auf einem Kanal auf Mobilgeräten.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Beispiel zeigt eine Bot-Tour in einem Kanal.":::

## <a name="chat-with-a-bot"></a>Chatten mit einem Bot

Bots werden direkt in das Messaging-Framework des Teams integriert. Benutzer können mit einem Bot chatten, um ihre Fragen zu beantworten, oder Befehle eingeben, damit der Bot eine enge oder bestimmte Gruppe von Aufgaben ausführt. Bots können Benutzer proaktiv per Chat über Änderungen oder Aktualisierungen Ihrer App informieren.

### <a name="chat-with-a-bot-in-different-contexts"></a>Chatten mit einem Bot in verschiedenen Kontexten

Sie können Bots in den folgenden Kontexten verwenden:

* **Persönliche Apps**: In einer persönlichen App verfügt ein Bot über eine eigene Chat-Registerkarte.
* **1:1-Chat**: Ein Benutzer kann eine private Unterhaltung mit einem Bot initiieren. Es ist die gleiche Erfahrung wie bei der Verwendung eines Bots in einer persönlichen App.
* **Gruppenchat**: Benutzer können mit einem Bot in einem Gruppenchat interagieren, indem sie den Bot @erwähnen.
* **Kanal**: Benutzer können mit einem Bot in einem Kanal interagieren. indem sie den Bot-Namen im Erstellungsfeld @erwähnen. Denken Sie daran, dass der Bot in diesem Zusammenhang dem gesamten Team zur Verfügung steht, nicht nur dem Kanal.

### <a name="anatomy"></a>Anatomie

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Mobilgerät Bots.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Name und -Symbol**|
|2|**Chat-Registerkarte**: Öffnet den Bereich für Gespräche mit Ihrem Bot (gilt nur für persönliche Apps).|
|3|**Benutzerdefinierte Registerkarten**: Öffnet weitere Inhalte zu Ihrer App.|
|4|**Chatblase**: Bot-Unterhaltungen verwenden das Messaging-Framework von Teams.|
|5|**Adaptive Karte**: Wenn die Antworten Ihres Bots Adaptive Karten enthalten, nimmt die Karte die volle Breite der Chatblase in Anspruch.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Bots.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Name und -Symbol**|
|2|**Chat-Registerkarte**: Öffnet den Bereich für Gespräche mit Ihrem Bot (gilt nur für persönliche Apps).|
|3|**Benutzerdefinierte Registerkarten**: Öffnet weitere Inhalte zu Ihrer App.|
|4|**Info-Registerkarte**: Zeigt grundlegende Informationen zu Ihrer App an.|
|5|**Chat-Blase**: Bot-Unterhaltungen verwenden das Team-Messaging-Framework.|
|6 |**Adaptive Karte**: Wenn die Antworten Ihres Bots Adaptive Karten enthalten, nimmt die Karte die volle Breite der Chatblase in Anspruch.|
|7 |**Befehlsmenü**: Zeigt die von Ihnen definierten Standardbefehle Ihres Bots an.|

### <a name="command-menu"></a>Befehlszeile

Das Befehlsmenü enthält eine Liste von Wörtern oder Begriffen, auf die Ihr Bot immer reagieren soll. Das Befehlsmenü wird über dem Verfassungsfeld angezeigt, wenn sich jemand mit einem Bot unterhält. Wenn ein Befehl ausgewählt ist, wird er in eine Nachricht eingefügt.

Die Liste der Befehle sollte kurz sein. Das Menü soll nur die wichtigsten Features Ihres Bots hervorheben. Halten Sie auch Befehle präzise. Erstellen Sie beispielsweise einen Befehl namens **Hilfe** anstelle von **Können Sie mir bitte helfen?**.

Das Befehlsmenü muss unabhängig vom Unterhaltungsstatus immer verfügbar sein.

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Beispiel zeigt das Befehlsmenü eines Bots.":::

## <a name="understand-what-people-are-saying"></a>Verstehen, was Personen sagen

Verwenden Sie einen Thesaurus und arbeiten Sie mit Personen mit möglichst vielen unterschiedlichen Hintergründen, um unterschiedliche Interpretationen von Standardabfragen zu generieren.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-hello.png" alt-text="Abbildung zeigt, wie ein Bot &quot;Hallo&quot; interpretieren könnte.":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-help.png" alt-text="Abbildung zeigt, wie ein Bot &quot;Hilfe&quot; interpretieren könnte.":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-thanks.png" alt-text="Abbildung zeigt, wie ein Bot &quot;Danke&quot; interpretieren könnte.":::
   :::column-end:::
:::row-end:::

### <a name="extract-intent-and-data-from-messages"></a>Extrahieren von Absichten und Daten aus Nachrichten

Entwerfen Sie Ihren Bot so, dass er Absichten erkennt, die erfassen, was jemand von einem Bot als Antwort auf eine Nachricht oder eine Anfrage erwartet. Intent klassifiziert eine Nachricht oder Abfrage als eine einzelne Aktion mit einem oder mehreren Datenobjekten, die von der Aktion betroffen sind.

Die folgenden Beispiele beschreiben die Benutzerabsicht und die Daten in Nachrichten, die an Bots gesendet wurden:

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-1.png" alt-text="Beispiel im Satz &quot;Flug nach Seattle buchen&quot;, Benutzerabsicht ist &quot;Flug buchen&quot; und Daten sind &quot;Seattle&quot;.":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-2.png" alt-text="Beispiel im Satz &quot;Wann öffnet das Geschäft?&quot; , die Benutzerabsicht lautet &quot;Wann&quot; und die Daten sind &quot;öffnet&quot;.":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-3.png" alt-text="Beispiel im Satz &quot;Besprechung planen mit Bob vom Vertrieb um 13:00 Uhr&quot;. Die Benutzerabsicht lautet &quot;Besprechung planen&quot; und die Daten lauten &quot;13:00 Uhr&quot; und &quot;Bob vom Vertrieb&quot;.":::
   :::column-end:::
:::row-end:::

### <a name="analyze-and-improve"></a>Analysieren und Verbessern

Erfahren Sie, was Benutzer sagen, wenn Sie mit Ihrem Bot chatten. Dies ist ein fortlaufender, iterativer Prozess, da Ihre Benutzerbasis an verschiedenen Standorten und in verschiedenen Organisationen wächst. Sie können die Spracherkennung und Absichtszuordnung Ihres Bots mit Microsoft Language Understanding (LUIS) optimieren.

* [Grundlegendes zu LUIS](/azure/cognitive-services/luis/artificial-intelligence): Erfahren Sie, wie LUIS AI verwendet, um Ihren App-Daten ein Verständnis von natürlicher Sprache (NLU) zu vermitteln.
* [Integration in LUIS](https://www.luis.ai/): Fügen Sie Ihrem Bot Funktionen in natürlicher Sprache hinzu, ohne den komplexen Prozess der Erstellung von Modellen für maschinelles Lernen.

## <a name="use-cases"></a>Anwendungsfälle

### <a name="simple-queries"></a>Einfache Abfragen

Bots bieten eine genaue Übereinstimmung mit einer Abfrage oder einer Gruppe verwandter Übereinstimmungen, um die Begriffsklärung zu erleichtern. Gruppieren Sie den Inhalt für verwandte Übereinstimmungen mithilfe einer Listenkarte.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrageinteraktion mit einem Bot auf einem Mobilgerät.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrageinteraktion mit einem Bot.":::

### <a name="multi-turn-interactions"></a>Mehrfach-Interaktionen

Während Ihr Bot vollständige Anfragen und Fragen unterstützen kann, sollte er auch in der Lage sein, Interaktionen mit mehreren Runden zu verarbeiten. Das Vorhersehen möglicher nächster Schritte erleichtert es den Mitarbeitern erheblich, einen vollständigen Aufgabenablauf durchzuführen (anstatt von ihnen zu erwarten, dass sie eine umfassende Anfrage erstellen).

In den folgenden Beispielen antwortet der Bot auf jede Nachricht mit Optionen für die nächsten Schritte.

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-multi-turn.png" alt-text="Beispiel zeigt eine Multi-Turn-Interaktion mit einem Bot auf einem Mobilgerät.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Beispiel zeigt eine Mehrfach-Interaktion mit einem Bot.":::

### <a name="reach-out-to-users"></a>Benutzer erreichen

Mit proaktiven Nachrichten kann sich Ihr Bot wie ein Digest verhalten, der mit einer bestimmten Häufigkeit Benachrichtigungen sendet, die für eine Person, einen Gruppenchat oder einen Kanal relevant sind. Ein Bot kann eine Nachricht senden, wenn sich etwas in einem Dokument geändert hat oder ein Arbeitselement geschlossen wird.

#### <a name="mobile"></a>Mobilgerät

Im folgenden Beispiel erhält der Benutzer eine Benachrichtigung, dass er von einem Bot auf einem anderen Kanal benachrichtigt wurde.

:::image type="content" source="../../assets/images/bots/mobile-bot-proactive-message-toast.png" alt-text="Beispiel zeigt ein Popup eines Bots, der einen Benutzer proaktiv über einen anderen Kanal vom Mobilgerät aus kontaktiert.":::

Nun kann der Benutzer auf diesem Kanal seine Nachricht vom Bot lesen.

:::image type="content" source="../../assets/images/bots/mobile-bot-proactive-message.png" alt-text="Beispiel zeigt, wie der Benutzer die proaktive Nachricht des Bots auf einem Mobilgerät betrachtet.":::

#### <a name="desktop"></a>Desktop

Im folgenden Beispiel erhält ein Benutzer eine Popup-Benachrichtigung, dass ein Bot ihn auf einem anderen Kanal benachrichtigt hat.

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Das Beispiel zeigt ein Popup eines Bots, der einen Benutzer proaktiv von einem anderen Kanal aus benachrichtigt.":::

Nun kann der Benutzer in diesem Kanal seine Nachricht des Bots lesen.

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Beispiel: Benutzer betrachtet die proaktive Nachricht des Bots.":::

### <a name="use-tabs-with-bots"></a>Verwenden von Registerkarten mit Bots

In persönlichen Apps kann eine Registerkarte die Möglichkeiten Ihres Bots ergänzen. Wenn Ihr Bot beispielsweise Arbeitsaufgaben erstellen kann, ist es gut, alle diese Elemente an einer zentralen Stelle innerhalb einer Registerkarte anzuzeigen. Weitere Informationen zum [Entwerfen von Registerkarten.](../../tabs/design/tabs.md)

#### <a name="mobile"></a>Mobilgerät

:::image type="content" source="../../assets/images/bots/mobile-bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte helfen kann, Botinhalte auf Mobilgeräten zu organisieren.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte beim Organisieren von Bot-Inhalten helfen kann.":::

## <a name="manage-a-bot"></a>Verwalten eines Bots

Benutzer sollten die Möglichkeit haben, die Einstellungen eines Bots zu ändern. Sie können diese Funktionalität mit Bot-Befehlen bereitstellen, aber in der Regel ist es effizienter, alle Einstellungen in ein [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)aufzunehmen (wie im folgenden Beispiel gezeigt).

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Beispiel zeigt ein Aufgabenmodul zum Konfigurieren der Einstellungen eines Bots.":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="content"></a>Inhalt

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Beispiel für eine bewährte Bot-Methode zum Einrichten einer klaren Persona.":::

#### <a name="do-establish-a-clear-persona"></a>Do: Erstellen einer eindeutigen Persona

Ist der Ton Ihres Bots freundlich und leicht, "nur die Fakten" oder super ungewöhnlich? Wie soll er in verschiedenen Szenarien reagieren? Das Planen und Dokumentieren der Persona Ihres Bots erleichtert das Schreiben von Antworten, die natürlich und zusammenhängend erscheinen.

Weitere Informationen zum Schreiben für Bots finden Sie im <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Beispiel, das deutlich zeigt, was Ihr Bot tun kann.":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a>Do: Vermitteln Sie eindeutig, was Ihr Bot alles kann.

Willkommensnachrichten und Touren helfen den Benutzern zu verstehen, was sie mit Ihrem Bot tun können.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Beispiel, das zeigt, dass die Features Ihres Bots nicht verdeckt werden sollten.":::

#### <a name="dont-obscure-your-bots-features"></a>Verdecken Sie nicht die Features Ihres Bots

Erste Eindrücke sind wichtig. Personen werden wahrscheinlich verwirrt oder misstrauisch sein, wenn sie eine nicht unbestimmbare Anmeldenachricht erhalten.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Beispiel, das zeigt, dass Ihr Bot Nicht-Fragen erkennen sollte.":::

#### <a name="do-recognize-non-questions"></a>Do: Nicht-Fragen erkennen

Ihr Bot sollte in der Lage sein, auf Nachrichten wie „Hallo“, „Hilfe“ und „Danke“ zu antworten und dabei auch gängige Rechtschreibfehler und umgangssprachliche Ausdrücke zu berücksichtigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Beispiel, das zeigt, dass Sie unübersichtliche Antworten auf einfache Botnachrichten vermeiden sollten.":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a>Don‘t: Keine Gelegenheit verpassen, die Freude schenkt

Einige Personen erwarten, dass Gespräche auf natürliche Weise ablaufen, so wie mit einer realen Person. Vermeiden Sie ungeschickte Antworten auf einfache Nachrichten.

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a>Problembehandlung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Beispiel, das zeigt, wie Bots Benutzern helfen sollen, die Verwendung von Bots zu verstehen.":::

#### <a name="do-provide-help"></a>Do: Hilfe anbieten

Wenn Ihr Bot eine Anfrage nicht erfüllen kann, bieten Sie einem Benutzer Möglichkeiten, sich über die Interaktion mit Ihrem Bot zu informieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Beispiel, das zeigt, dass Ihr Bot keine Benutzer stranden sollte.":::

#### <a name="dont-leave-users-stranded"></a>Don‘t: Lassen Sie Benutzer nicht hängen

Benutzer werden Ihren Bot schnell verlassen, wenn er keine Probleme beheben kann.

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a>Komplexe Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Beispiel, das zeigt, dass Sie Aufgabenmodule oder Registerkarten mit Ihrem Bot für komplexe Interaktionen verwenden können.":::

#### <a name="do-use-task-modules-or-tabs"></a>Do: Verwenden Sie Aufgabenmodule oder Registerkarten

Wenn Ihr Bot eine Antwort liefert, die einige weitere Schritte erfordert, können Sie eine Verknüpfung zu einem Aufgabenmodul oder einer Registerkarte herstellen, um die Aufgabe oder den Ablauf abzuschließen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Beispiel, das zeigt, wie Ihr Bot Interaktionen mit mehreren Wendungen vermeiden sollte.":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a>Don‘t: Machen Sie Mehrfach-Interaktionen nicht langweilig

Eine umfassende Unterhaltung zum Abschließen einer einzelnen Aufgabe ist langsam und übermäßig komplex. Außerdem muss der Entwickler Statusänderungen berücksichtigen (z. B. das Zeitlimit der Unterhaltung oder das Senden einer Nachricht zum Abbrechen).

   :::column-end:::
:::row-end:::

### <a name="privacy"></a>Datenschutz

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Beispiel, das zeigt, wie Bots nur private Informationen in einem persönlichen Kontext anzeigen sollen.":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a>Do: Zeigen Sie vertrauliche Informationen nur in einem persönlichen Kontext an

Wenn sich Ihr Bot in einem Gruppenchat oder -kanal befindet, empfehlen wir, Benutzer an einen privaten Ort (z. B. ein Aufgabenmodul, eine Registerkarte oder einen Browser) zu leiten, um vertrauliche Informationen anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Beispiel, wie Bots vertrauliche Informationen nicht für eine Gruppe oder Personen offenlegen sollten.":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a>Don‘t: Einige Inhalte sollten nicht für alle einsehbar sein

Ihr Bot sollte keine vertraulichen Informationen an Personen in einer Gruppe weitergeben.

   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Siehe auch

Diese weiteren Richtlinien könnten bei Ihrem Bot-Design hilfreich sein:

* [Entwerfen Ihrer persönlichen App](../../concepts/design/personal-apps.md)
* [Entwerfen Adaptiver Karten](../../task-modules-and-cards/cards/design-effective-cards.md)
* [Entwerfen von Aufgabenmodulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
