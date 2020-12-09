---
title: Entwerfen Ihres bot
description: Hier erfahren Sie, wie Sie einen Teams-bot entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d1a7470f4986de22ecca7071823b620cb0234abb
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605427"
---
# <a name="designing-your-microsoft-teams-bot"></a>Entwerfen Ihres Microsoft Teams-bot

Bots sind Unterhaltungs-apps, die eine bestimmte Gruppe von Aufgaben ausführen. Basierend auf dem <a href="https://dev.botframework.com/" target="_blank">Microsoft-bot-Framework</a>kommunizieren Bots mit Benutzern, Antworten auf Ihre Fragen und informieren Sie proaktiv über Änderungen und andere Ereignisse. Sie sind eine großartige Möglichkeit, um Sie zu erreichen.

Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Bots in Microsoft Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Ausführlichere bot-Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-bot"></a>Hinzufügen eines bot

Bots stehen in Chats, Kanälen und persönlichen Apps zur Verfügung. Sie können einen bot einer der folgenden Möglichkeiten hinzufügen:

* Aus dem Microsoft Teams Store (AppSource).
* Verwenden des App-Flyouts, indem Sie das Symbol **Weitere** auf der linken Seite von Teams auswählen.
* Mit einem @mention im Feld Neuer Chat oder verfassen (im folgenden Beispiel wird gezeigt, wie Sie dies in einem Gruppenchat tun können).

:::image type="content" source="../../assets/images/bots/add-bot-chat-at-mention.png" alt-text="Beispiel zeigt, wie ein bot in einem Gruppenchat mithilfe eines @mention hinzugefügt wird." border="false":::

## <a name="introduce-a-bot"></a>Einführung eines bot

Es ist wichtig, dass sich Ihr bot selbst vorstellt und beschreibt, was er tun kann. Diese anfängliche Exchange hilft den Benutzern zu verstehen, was mit dem bot zu tun ist, um seine Einschränkungen herauszufinden und, was am wichtigsten ist, eine bequeme Interaktion mit ihm zu erhalten.

### <a name="welcome-message-in-a-one-on-one-chat"></a>Willkommensnachricht in einem Einzelchat

In persönlichen Kontexten legen Begrüßungsnachrichten den Ton Ihres bot fest. Die Nachricht enthält eine Begrüßung, was der bot tun kann, und einige Vorschläge für die Interaktion (beispielsweise "versuchen Sie, mich zu Fragen..."). Wenn möglich, sollten diese Vorschläge gespeicherte Antworten zurückgeben, ohne sich anzumelden.

:::image type="content" source="../../assets/images/bots/bot-personal-welcome.png" alt-text="Beispiel zeigt eine bot-Einführung in einer persönlichen app." border="false":::

### <a name="introductions-in-group-chats-and-channels"></a>Einführungen in Gruppenchats und-Kanälen

Die Einführung Ihres bot sollte in Gruppenchats und Kanälen im Vergleich zu einem persönlichen Kontext (wie einer persönlichen APP) geringfügig unterschiedlich sein. Im wirklichen Leben, wenn Sie einen Raum voller Personen betraten; Sie würden sich vorstellen, anstatt alle Personen, die bereits dort sind, zu begrüßen. Tragen Sie dieses Denken in Ihr bot-Design.

:::image type="content" source="../../assets/images/bots/bot-group-welcome.png" alt-text="Beispiel zeigt eine bot-Einführung in einen kollaborativen Kontext." border="false":::

### <a name="bot-authentication-with-single-sign-on"></a>Bot-Authentifizierung mit einmaligem Anmelden

Wenn eine Person einen bot Nachrichten kann, müssen Sie unter Umständen alle ihre Funktionen verwenden. Sie können den Authentifizierungsprozess mithilfe von einmaligem Anmelden (Single Sign-on, SSO) vereinfachen.

Vergessen Sie nicht: im bot-Befehlsmenü (**Was kann ich tun?**) müssen Sie auch einen Befehl zur Abmeldung bereitstellen.

:::image type="content" source="../../assets/images/bots/bot-sso-example.png" alt-text="Beispiel zeigt einen bot mit einer Anmeldeschaltfläche." border="false":::

### <a name="tours"></a>Touren

Sie können eine Tour mit Begrüßungsnachrichten einschließen, und wenn der bot auf etwas wie einen "Help"-Befehl reagiert. Eine Tour ist die effektivste Möglichkeit, um zu beschreiben, was Ihr bot tun kann. Wenn zutreffend, eignen Sie sich auch hervorragend für die Beschreibung der anderen Features Ihrer APP (beispielsweise Screenshots Ihrer Messaging Erweiterung).

> [!IMPORTANT]
> Auf Touren sollte zugegriffen werden, ohne dass Sie sich anmelden müssen.

#### <a name="one-on-one-chats"></a>Eins-zu-eins-Chats

In einer persönlichen App kann ein Karussell einen effektiven Überblick über Ihren bot und andere Features Ihrer APP bieten. Einschließlich Schaltflächen die Benutzer können bot-Befehle versuchen, wird empfohlen (beispielsweise **Erstellen einer Aufgabe**).

:::image type="content" source="../../assets/images/bots/bot-tour-personal.png" alt-text="Beispiel zeigt eine bot-Tour in einem Einzelchat." border="false":::

#### <a name="channels-and-group-chats"></a>Kanäle und Gruppenchats

In Kanälen und Gruppenchats sollte ein Rundgang in einem modalen (auch als [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) bezeichnet) geöffnet werden, damit keine laufenden Unterhaltungen unterbrochen werden. Dadurch erhalten Sie auch die Möglichkeit, rollenbasierte Ansichten für Ihre Tour zu implementieren.

:::image type="content" source="../../assets/images/bots/bot-tour-channel.png" alt-text="Beispiel zeigt eine bot-Tour in einem Kanal." border="false":::

## <a name="chat-with-a-bot"></a>Chat mit einem bot

Bots können direkt in das Messaging Framework von Teams integriert werden. Benutzer können mit einem bot chatten, um Ihre Fragen zu beantworten, oder Befehle eingeben, damit der bot einen engen oder bestimmten Aufgabensatz ausführen kann. Bots können Benutzer proaktiv über Änderungen oder Aktualisierungen Ihrer APP per Chat informieren.

### <a name="chat-with-a-bot-in-different-contexts"></a>Chatten mit einem bot in unterschiedlichen Kontexten

Sie können Bots in den folgenden Kontexten verwenden:

* **Persönliche apps**: in einer persönlichen App verfügt ein bot über eine dedizierte Chat-Registerkarte.
* **Eins-zu-eins-Chat**: ein Benutzer kann eine private Unterhaltung mit einem bot initiieren. Es ist die gleiche Erfahrung wie die Verwendung eines bot in einer persönlichen app.
* **Gruppenchat**: Personen können mit einem bot in einem Gruppenchat interagieren, indem Sie den bot @mentioning.
* **Kanal**: Personen können mit einem bot in einem Kanal interagieren. durch @mentioning des Namens des bot im Feld Verfassen. Denken Sie daran, dass der bot in diesem Zusammenhang für das gesamte Team und nicht nur für den Kanal verfügbar ist.

### <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/bots/bot-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines bot." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Name und Symbol**|
|2 |**Registerkarte Chat**: öffnet den Raum für Gespräche mit Ihrem bot (gilt nur für persönliche Apps).|
|3 |**Benutzerdefinierte Registerkarten**: öffnet andere Inhalte im Zusammenhang mit Ihrer APP.|
|4 |Informationen **zur Registerkarte**: zeigt grundlegende Informationen zu Ihrer APP an.|
|5 |**Chat Blase**: bot-Unterhaltungen verwenden das Teams-Messaging Framework.|
|6 |**Adaptive Karte**: Wenn die Antworten Ihres bot Adaptive Karten enthalten, nimmt die Karte die gesamte Breite der Chat Blase an.|
|7 |**Befehlsmenü**: zeigt die Standardbefehle Ihres bot an (definiert von Ihnen).

### <a name="command-menu"></a>Befehlsmenü

Das Befehlsmenü enthält eine Liste von Wörtern oder Ausdrücken, auf die ihr bot immer antworten soll. Das Befehlsmenü wird über dem Feld Verfassen angezeigt, wenn jemand mit einem bot in Gespräch kommt. Wenn ein Befehl ausgewählt wird, wird er in eine Nachricht eingefügt.

Die Liste der Befehle sollte kurz sein. Das Menü ist nur dazu gedacht, die primären Funktionen Ihres bot hervorzuheben. Halten Sie die Befehle auch prägnant. Erstellen Sie beispielsweise einen Befehl namens " **Help** " anstelle von **können Sie mir bitte helfen**?
Das Befehlsmenü muss unabhängig vom Status der Unterhaltung immer verfügbar sein.

:::image type="content" source="../../assets/images/bots/bot-command-menu.png" alt-text="Beispiel zeigt das Befehlsmenü eines bot." border="false":::

## <a name="understand-what-people-are-saying"></a>Verstehen, was die Leute sagen

Verwenden Sie einen Thesaurus, und rufen Sie Personen aus so vielen verschiedenen Hintergründen ab, die Sie bei der Generierung unterschiedlicher Interpretationen von Standardabfragen unterstützen.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-hello.png" alt-text="Illustration, die zeigt, wie ein bot möglicherweise &quot;Hello&quot; interpretiert." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-help.png" alt-text="Illustration, die zeigt, wie ein bot die &quot;Hilfe&quot; interpretieren kann." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-understanding-thanks.png" alt-text="Illustration, die zeigt, wie ein bot vielleicht &quot;Danke&quot; interpretiert." border="false":::
   :::column-end:::
:::row-end:::

### <a name="extract-intent-and-data-from-messages"></a>Extrahieren von Absichtserklärungen und Daten aus Nachrichten

Entwerfen Sie Ihren bot, um Absichtserklärungen zu erkennen, wodurch erfasst wird, was jemand von einem bot als Reaktion auf eine Nachricht oder Abfrage wünscht. Intent klassifiziert eine Nachricht oder Abfrage als einzelne Aktion mit einem oder mehreren Datenobjekten, die von der Aktion betroffen sind. 

In den folgenden Beispielen werden die Benutzerabsicht und die Daten in Nachrichten, die an Bots gesendet werden, umrissen.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-1.png" alt-text="Beispiel im Satz &quot;Buchen eines Flugs nach Seattle&quot; zeigt die Benutzerabsicht &quot;Flug buchen&quot; und die Daten sind &quot;Seattle&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-2.png" alt-text="Beispiel im Satz &quot;Wenn der Speicher geöffnet wird&quot; ist die Benutzerabsicht &quot;When&quot; und die Daten sind &quot;Open&quot;." border="false":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-intent-3.png" alt-text="Beispiel im Satz &quot;Planen einer Besprechung am 13.00 Uhr mit Bob in der Verteilung&quot; angezeigt wird, ist die Benutzerabsicht &quot;Besprechung planen&quot; und die Daten sind &quot;13.00&quot; und &quot;Bob in Distribution&quot;." border="false":::
   :::column-end:::
:::row-end:::

### <a name="analyze-and-improve"></a>Analysieren und verbessern

Erfahren Sie, was Benutzer sagen, wenn Sie mit Ihrem bot chatten. Dies wird ein fortlaufender, iterativer Prozess, wenn Ihre Benutzerbasis an unterschiedlichen Standorten und Organisationen wächst. Sie können die Spracherkennung und die Absicht-Zuordnung Ihres bot mit Microsoft Language Understanding (Luis) optimieren.

* [Understanding Luis](https://docs.microsoft.com/azure/cognitive-services/luis/artificial-intelligence): erfahren Sie, wie Luis AI verwendet, um Ihre APP-Daten mit natürlichen Sprachkenntnissen (NLU) zu versorgen.
* [Integration mit Luis](https://www.luis.ai/): Fügen Sie Ihrem bot natürliche Sprachfunktionen hinzu, ohne dass ein komplexer Prozess zum Erstellen von maschinellen Lernmodellen vorliegt.

## <a name="use-cases"></a>Anwendungsfälle

### <a name="simple-queries"></a>Einfache Abfragen

Bots können eine exakte Übereinstimmung mit einer Abfrage oder einer Gruppe verwandter Übereinstimmungen zur Unterstützung der Begriffsklärung liefern. Gruppieren Sie bei Verwandten Übereinstimmungen den Inhalt mithilfe einer Listen Karte.

:::image type="content" source="../../assets/images/bots/bot-simple-query.png" alt-text="Beispiel zeigt eine einfache Abfrage Interaktion mit einem bot." border="false":::

### <a name="multi-turn-interactions"></a>Multi-Turn-Interaktionen

Während Ihr bot vollständige Anfragen und Fragen unterstützenkann, sollte er auch Multi-Turn-Interaktionen verarbeiten können. Die Vorwegnahme möglicher nächster Schritte macht es für Personen viel einfacher, einen vollständigen Aufgabenfluss zu planen (statt zu erwarten, dass Sie eine umfassende Anforderung fertig stellen).

Im folgenden Beispiel reagiert der bot auf jede Nachricht mit Optionen für das, was als nächstes möglicherweise gewünscht wird.

:::image type="content" source="../../assets/images/bots/bot-multi-turn.png" alt-text="Beispiel zeigt eine Multi-Turn-Interaktion mit einem bot." border="false":::

### <a name="reach-out-to-users"></a>Erreichen von Benutzern

Mit proaktivem Messaging kann Ihr bot wie ein Digest fungieren, der Benachrichtigungen für eine Person, einen Gruppenchat oder einen Kanal mit einer bestimmten Frequenz sendet. Ein Bot kann eine Nachricht senden, wenn sich etwas in einem Dokument geändert hat oder wenn ein Arbeitselement geschlossen ist.

Im folgenden Beispiel erhält ein Benutzer eine Popupbenachrichtigung, die von einem bot in einem anderen Kanal gesendet wurde.

:::image type="content" source="../../assets/images/bots/bot-proactive-message-toast.png" alt-text="Beispiel zeigt einen Toast eines bot-proaktiven Messaging eines Benutzers aus einem anderen Kanal." border="false":::

Der Benutzer kann nun in diesem Kanal seine Nachricht vom bot lesen.

:::image type="content" source="../../assets/images/bots/bot-proactive-message.png" alt-text="Das Beispiel zeigt, wie der Benutzer die proaktive Nachricht des bot sucht." border="false":::

### <a name="use-tabs-with-bots"></a>Verwenden von Tabs mit Bots

Eine Registerkarte kann Ihren bot einfacher zu verwenden. Wenn Ihr bot beispielsweise Arbeitsaufgaben erstellen kann, wäre es schön, alle diese Elemente an einer zentralen Stelle in einer Registerkarte anzuzeigen. Weitere Informationen finden Sie unter [Entwerfen von Registerkarten](../../tabs/design/tabs.md).

:::image type="content" source="../../assets/images/bots/bot-with-tab.png" alt-text="Beispiel zeigt, wie eine Registerkarte helfen kann, bot-Inhalte zu organisieren." border="false":::

## <a name="manage-a-bot"></a>Verwalten eines bot

Benutzer sollten in der Lage sein, die Einstellungen eines bot zu ändern. Sie können diese Funktionalität mit bot-Befehlen bereitstellen, es ist jedoch in der Regel effizienter, alle Einstellungen in einem [Aufgabenmodul](../../task-modules-and-cards/task-modules/design-teams-task-modules.md) einzuschließen (wie im folgenden Beispiel dargestellt).

:::image type="content" source="../../assets/images/bots/manage-bot-task-module.png" alt-text="Beispiel zeigt ein Aufgabenmodul zum Konfigurieren der Einstellungen eines bot." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

### <a name="content"></a>Inhalt

:::image type="content" source="../../assets/images/bots/bot-content-persona-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-establish-a-clear-persona"></a>Do: Erstellen einer eindeutigen Rolle

Ist Ihr bot Ton freundlich und leicht, "nur die Fakten" oder Super schrullig? Wie sollte Sie in unterschiedlichen Szenarien reagieren? Das Planen und Dokumentieren der Persona Ihres bot erleichtert das Schreiben von Antworten, die natürlich und zusammenhängend wirken.

Weitere Informationen zum Schreiben von Bots finden Sie im <a href="https://www.figma.com/community/file/916836509871353159" target="_blank">Microsoft Teams UI Kit (Figma).</a>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-clearly-convey-what-your-bot-can-do"></a>Do: deutlich vermitteln, was Ihr bot tun kann

Begrüßungsnachrichten und-Touren helfen Benutzern zu verstehen, was Sie mit Ihrem bot tun können.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-convey-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-obscure-your-bots-features"></a>Nicht: verdecken der Funktionen Ihres bot

Erste Eindrücke sind wichtig. Personen werden wahrscheinlich verwirrt oder misstrauisch, wenn Sie mit einer unscheinbaren Anmeldenachricht angezeigt werden.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-recognize-non-questions"></a>Do: Erkennen von nicht-Fragen

Ihr bot sollte in der Lage sein, auf Nachrichten wie "Hi", "Help" und "Thanks" zu Antworten und gleichzeitig häufige Rechtschreibfehler und Colloquialisms zu berücksichtigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-content-understand-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-miss-out-on-opportunities-to-delight"></a>Nicht: Gelegenheiten zur Freude verpassen

Einige Leute erwarten, dass Unterhaltungen natürlich wie bei einer realen Person fließen. Versuchen Sie, ungeschickte Antworten auf einfache Nachrichten zu vermeiden.

   :::column-end:::
:::row-end:::

### <a name="troubleshooting"></a>Problembehandlung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-provide-help"></a>Do: Hilfe bereitstellen

Wenn Ihr bot eine Anforderung nicht erfüllen kann, bieten Sie Möglichkeiten für einen Benutzer, sich über die Interaktion mit Ihrem bot zu informieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-help-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-leave-users-stranded"></a>Nicht: lassen Sie die Benutzer gestrandet

Personen werden Ihren bot schnell verlassen, wenn Sie Probleme nicht beheben können.

   :::column-end:::
:::row-end:::

### <a name="complex-interactions"></a>Komplexe Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-use-task-modules-or-tabs"></a>Do: Verwenden von Aufgaben Modulen oder Registerkarten

Wenn Ihr bot eine Antwort enthält, die ein paar weitere Schritte erfordert, können Sie einen Link zu einem Aufgabenmodul oder einer RegisterkarteErstellen, um den Vorgang oder den Ablauf abzuschließen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-interactions-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-make-multi-turn-interactions-tedious"></a>Nicht: machen Sie Multi-Turn-Interaktionen langweilig

Eine umfassende Unterhaltung zum Ausführen einer einzelnen Aufgabe ist langsam und übermäßig Komplex. Außerdem muss der Entwicklerstatus Änderungen berücksichtigen (beispielsweise das Timeout bei der Unterhaltung oder das Senden einer "Cancel"-Nachricht).

   :::column-end:::
:::row-end:::

### <a name="privacy"></a>Datenschutz

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-do.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="do-only-show-sensitive-info-in-a-personal-context"></a>Do: nur vertrauliche Informationen in einem persönlichen Kontext anzeigen

Wenn sich Ihr bot in einem Gruppenchat oder-Kanal befindet, empfehlen wir, Benutzer zu einem privaten Speicherort (wie einem Aufgabenmodul, einer Registerkarte oder einem Browser) zu leiten, um vertrauliche Informationen anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/bots/bot-privacy-dont.png" alt-text="Beispiel, das eine bot-bewährte Methode zeigt." border="false":::

#### <a name="dont-some-content-isnt-meant-to-be-seen-by-everyone"></a>Nicht: einige Inhalte werden nicht für alle sichtbar sein sollen.

Ihr bot sollte keine vertraulichen Informationen für eine Gruppe von Personen offen legen.

   :::column-end:::
:::row-end:::

## <a name="learn-more"></a>Mehr erfahren

Diese anderen Richtlinien können bei Ihrem bot-Design hilfreich sein:

* [Entwerfen Ihrer persönlichen App](../../concepts/design/personal-apps.md)
* [Entwerfen adaptiver Karten](../../task-modules-and-cards/cards/design-effective-cards.md)
* [Entwerfen von Aufgaben Modulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
