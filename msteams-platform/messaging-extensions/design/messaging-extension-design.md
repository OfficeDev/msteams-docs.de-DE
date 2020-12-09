---
title: Entwerfen Ihrer Messaging Erweiterung
description: Erfahren Sie, wie Sie eine Teams-Messaging Erweiterung entwerfen und das Microsoft Teams UI Kit erhalten.
keywords: Design Guidelines für Teams Referenz Tipps für Messaging-Erweiterungen bewährte Methode
author: heath-hamilton
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ad628bdaa46058aed4acdcea1a224c7ebfe40f89
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604853"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Entwerfen Ihrer Microsoft Teams-Messaging Erweiterung

Messaging-Erweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln in einer Nachricht, ohne von der Unterhaltung Weg zu navigieren.

Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie Personen Messaging Erweiterungen in Microsoft Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Entwurfsrichtlinien für Messaging-Erweiterungen, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Hinzufügen einer Messaging Erweiterung

Sie können eine Messaging Erweiterung in den folgenden Microsoft Teams-Kontexten hinzufügen:

* Aus dem Microsoft Teams Store (AppSource).
* In einem Kanal, Chat oder einer Besprechung (vor, während und nach) in der Nähe des Felds zum Verfassen. Es ist erwähnenswert, wenn Sie eine Messaging Erweiterung an einer dieser Orte hinzufügen, nur Sie können Sie in diesem Kontext verwenden.

Im folgenden Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung in einem Kanal hinzufügen.

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="In diesem Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung neben dem Feld Verfassen in einem Kanal hinzufügen." border="false":::

## <a name="set-up-a-messaging-extension"></a>Einrichten einer Messaging Erweiterung

Die Authentifizierung ist nicht zwingend erforderlich, aber wenn Ihre APP so etwas wie ein Ticket verfolgungstool ist, müssen sich möglicherweise Benutzer anmelden, um die Messaging Erweiterung zu verwenden.

Für Konsistenz in Microsoft Teams-Apps können Sie den Anmeldebildschirm nicht anpassen. Wenn Sie die SSO-Authentifizierung (Single Sign-on, einmaliges Anmelden) verwenden, werden Benutzer automatisch angemeldet.

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Beispiel zeigt den Setupbildschirm für die Messaging Erweiterung mit einer Anmeldeschaltfläche." border="false":::

## <a name="types-of-messaging-extensions"></a>Typen von Messaging Erweiterungen

Messaging Erweiterungen können Suchbefehle, Aktionsbefehle oder beides haben. Ihre Befehle hängen von den Funktionen Ihrer APP ab und davon, wie diese in Microsoft Teams-Anwendungsfällen angepasst werden.

### <a name="search-commands"></a>Suchbefehle

Mit Suchbefehlen können Benutzer Ihre Messaging Erweiterung verwenden, um schnell externe Inhalte zu finden und in eine Nachricht einzufügen. Suchbefehle werden häufig im Feld Verfassen zur Verfügung gestellt. Sie können beispielsweise eine Diskussion starten oder hinzufügen, indem Sie einen Teil des Inhalts freigeben, ohne Teams jemals verlassen zu müssen.

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Beispiel zeigt eine suchbasierte Messaging Erweiterung, die im Feld erstellen gestartet wurde." border="false":::

#### <a name="compose-box-layout-options"></a>Optionen für das Erstellen von Feldlayouts

Sie haben einige Optionen zum Anzeigen von Suchergebnissen für Messaging Erweiterungen, einschließlich [Listen-und rasteransichten](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Illustrationen mit Layout-Optionen für Suchergebnisse der Messaging-Erweiterung." border="false":::

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle ermöglichen Benutzern das Auslösen von Aktionen und Verarbeiten von Anforderungen in externen Diensten in Microsoft Teams. Wenn Ihre APP beispielsweise Bestellungen aufspürt, könnte ein Benutzer eine neue Bestellung mit dem Inhalt der Nachricht eines Kollegen von rechts in seinem Chat erstellen.

Bei Aktionen basierenden Messaging Erweiterungen ist es häufig erforderlich, dass Benutzer ein Formular oder eine andere Art von Konfiguration innerhalb eines modalen Formulars ausfüllen. Sie können diese Erfahrungen mit [Aufgaben Modulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.

## <a name="open-a-messaging-extension"></a>Öffnen einer Messaging Erweiterung

Das Feld "Verfassen" und "Nachrichten/Beiträge" sind die primären Kontexte, in denen Personen Messaging Erweiterungen verwenden.

### <a name="from-the-compose-box"></a>Aus dem Feld Verfassen

Sobald die Benutzer hinzugefügt wurden, können Sie Ihre Messaging Erweiterung öffnen, indem Sie das App-Symbol unter dem Feld Verfassen auswählen. In diesem Beispiel verfügt die Erweiterung über Such-und Aktionsbefehle.

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="In diesem Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung aus dem Feld Verfassen öffnen." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a>Aus einer Chatnachricht oder einem Kanal Beitrag

Nachdem die Benutzer hinzugefügt wurden **More** , können Sie :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chatnachricht oder im Kanal Beitrag das Symbol "More" auswählen, um die Aktionsbefehle ihrer Erweiterung zu finden. Ihre Erweiterung wird möglicherweise unter **Weitere Aktionen** basierend auf der Verwendung aufgeführt.

#### <a name="chat-message"></a>Chatnachricht

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Beispiel zeigt, wie Sie eine Messaging Erweiterung aus einer Chatnachricht öffnen." border="false":::

#### <a name="channel-post"></a>Kanal Beitrag

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="In diesem Beispiel wird gezeigt, wie Sie eine Messaging Erweiterung von einem Kanal Beitrag aus öffnen." border="false":::

## <a name="use-a-messaging-extension"></a>Verwenden einer Messaging Erweiterung

In den folgenden Szenarien werden die primären Methoden für die Verwendung von Messaging Erweiterungen gezeigt.

### <a name="insert-content-into-a-message"></a>Einfügen von Inhalt in eine Nachricht

**1. Wählen Sie eine Messaging Erweiterung aus**. Benutzer können im Feld Verfassen nach dem Inhalt suchen, den Sie freigeben möchten.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Beispiel: ein Benutzer, der nach einzufügenden Inhalten sucht, wird aus dem Feld Verfassen angezeigt." border="false":::

**2. Einfügen von Inhalten**. Nach der Veröffentlichung können andere Personen Antworten oder den Inhalt auswählen, um weitere Informationen in Ihrer APP anzuzeigen.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Beispiel zeigt einen Benutzer, der Inhalte in einer Kanal Unterhaltung veröffentlicht." border="false":::

### <a name="take-action-on-a-message"></a>Aktion für eine Nachricht ausführen

**1. Wählen Sie eine Messaging Erweiterung aus**. Ihre APP kann einen oder mehrere Aktionsbefehle enthalten.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Beispiel zeigt einen Benutzer, der einen Aktionsbefehl für die Messaging Erweiterung auswählt." border="false":::

**2. führen Sie die Aktion** aus. Ihre APP kann alle Inhalte oder Daten, die von der Nachrichtenaktion gesendet werden, empfangen und verarbeiten. Auf diese Weise können Benutzer in Ihrer Unterhaltung bleiben, und im folgenden Beispiel wird keine direkte Eingabe von Informationen in Ihre APP befürchtet.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel: ein Benutzer, der nach einzufügenden Inhalten sucht, wird aus dem Feld Verfassen angezeigt." border="false":::

### <a name="preview-links"></a>Vorschau Links

Mithilfe von Messaging Erweiterungen können Sie auch Rich-Links von einer erkannten URL in eine Nachricht einfügen (diese Funktion wird als [Verknüpfungs Entfaltung](../../messaging-extensions/how-to/link-unfurling.md)bezeichnet).

**1. Fügen Sie einen erkannten Link** in das Feld Verfassen ein.

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Beispiel zeigt ein Benutzer, der einen Link in das Feld Kompost einfügt." border="false":::

**2. Einfügen von Inhalten**. Wenn Ihre APP die URL im Feld Verfassen erkennt, wird die Verknüpfung als Karte gerendert, die eine inhaltsreiche Vorschau des Webinhalts bereitstellt. (Weitere Informationen finden Sie unter [Adaptive Cards Design Guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) .)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Beispiel zeigt, wie die URL, da Sie von Ihrer APP erkannt wird, einen umfangreichen Inhalt im Feld Verfassen enthält." border="false":::

## <a name="manage-a-messaging-extension"></a>Verwalten einer Messaging Erweiterung

Wenn Sie mit der rechten Maustaste auf Ihr Symbol klicken, können Benutzer Ihre Messaging Erweiterung anheften, entfernen oder konfigurieren.

## <a name="anatomy"></a>Anatomie

### <a name="messaging-extension-in-the-compose-box"></a>Messaging Erweiterung im Feld Verfassen

Das folgende Beispiel ist eine im Feld Verfassen geöffnete Messaging Erweiterung.

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Illustration, die die Benutzeroberflächen Anatomie einer Messaging Erweiterung im Feld Verfassen zeigt." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo**: Farbsymbol des App-Logos.|
|2 |**App-Name**: vollständiger Name Ihrer APP.|
|3 |**Menüsymbol für Aktionsbefehle (optional)**: öffnet eine Liste mit Aktions Befehlen für Ihre Messaging Erweiterung (wenn Sie eine beliebige Option angeben).
|4 |**Suchfeld**: ermöglicht Benutzern das Auffinden von App-Inhalten, die Sie einfügen möchten.|
|5 |**Tab-Menü (optional)**: bietet mehrere Inhaltskategorien.|
|6 |**Menü "Aktionsbefehle" (optional)**: zeigt eine Liste der Aktionsbefehle an (sofern angegeben).|
|7 |**App-Inhalt**: in erster Linie zum Anzeigen von Suchergebnissen. Im Beispiel wird das Listenlayout verwendet (das Rasterlayout ist eine weitere Option).|
|8 |**App-Logo**: Gliederungssymbol des App-Logos.|

### <a name="messaging-extension-management-menu"></a>Menü "Messaging-Erweiterungsverwaltung"

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung der UI-Anatomie eines Messaging-Erweiterungs Verwaltungsmenüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Unpin**: verfügbar, wenn der Benutzer Ihre APP angeheftet hat.|
|2 |**Remove**: entfernt die Messaging Erweiterung aus dem Kanal, dem Chat oder der Besprechung.|

## <a name="best-practices"></a>Bewährte Methoden

### <a name="setup-and-general-usage"></a>Setup und allgemeine Verwendung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Do: integrieren in einmaliges Anmelden

Mit SSO wird der Anmeldeprozess einfacher, schneller und sicherer. Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich auch nicht erneut anmelden, um auf die Messaging Erweiterung zuzugreifen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Nicht: Benutzer von der Unterhaltung entfernen

Bei Messaging Erweiterungen handelt es sich um Verknüpfungen, die den Kontextwechsel reduzieren sollen. Ihre Erweiterung sollte beispielsweise keine Benutzer zu einer Webseite außerhalb von Teams weiterleiten.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Do: Markieren Sie Ihre Messaging-Erweiterung

Messaging Erweiterungen sind nicht immer leicht zu finden. Fügen Sie Screenshots zur Verwendung in Ihrer APP-Detailseite hinzu. Wenn Ihre APP auch einen bot enthält, können Sie die Hilfedokumentation zur Messaging Erweiterung in eine bot-Willkommens Tour einbeziehen.

### <a name="templating"></a>Vorlagen hinzu

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Do: Teams können einen Teil des Entwurfs bearbeiten, wenn möglich

Wenn es für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messaging Erweiterung erstellen. Microsoft Teams rendert diese Erweiterungstypen mit integrierter Gestaltung und Barrierefreiheit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Nicht: bettet die gesamte app in ein Aufgabenmodul ein.

Wenn Ihre Messaging-Erweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul einfach, und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Do: nutzen Sie die Vorteile von Microsoft Teams-Farb Token

Jedes Microsoft Teams-Design verfügt über ein eigenes Farbschema. Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farb Token (Fluent UI)</a> in Ihrem Design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-hard-code-color-values"></a>Nicht: Farb Werte mit festem Code

Wenn Sie keine Microsoft Teams-Farb Token verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit zum Verwalten.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Do: Aktionsbefehle einschließen, die im Kontext sinnvoll sind

Nachrichten Aktionen sollten sich auf das beziehen, was ein Benutzer sucht. Stellen Sie beispielsweise Benutzern eine Verknüpfung zum Erstellen eines Problems oder einer Arbeitsaufgabe mit dem Text im Beitrag eines anderen Benutzers bereit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel mit einer bewährten Methode für die Messaging Erweiterung." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Nicht: Aktionsbefehle einbeziehen, die nicht kontextbezogen sind

Eine Nachrichtenaktion zum **Anzeigen des Dashboards** würde wahrscheinlich von den meisten Unterhaltungen getrennt erscheinen.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Sucht

#### <a name="do-show-search-results-while-typing"></a>Do: Suchergebnisse bei der Eingabe anzeigen

Stellen Sie vorgeschlagene Suchergebnisse bereit, während Benutzer eingeben. Sie finden möglicherweise den benötigten Inhalt schneller bei minimaler Anzahl von Zeichen.

#### <a name="dont-require-users-to-submit-a-query"></a>Nicht: Benutzer müssen eine Abfrage senden

Sie können festlegen, dass Benutzer eine Taste drücken oder eine Schaltfläche auswählen, um Abfragen an Ihre APP zu senden. Dies ist zwar für Ihren app-Dienste-Dienst möglicherweise einfacher, aber die Benutzer werden möglicherweise verwechselt, dass Sie beim eingeben keine Echtzeitsuchergebnisse sehen.

#### <a name="do-consider-zero-term-queries"></a>Do: in Frage stellen von NULL-Term-Abfragen

Wenn ein Benutzer beispielsweise eine beliebige Person in das Suchfeld schreibt, zeigen Sie an, was diese zuletzt in ihrer App angezeigt haben. Es ist möglich, dass Sie diese Inhalte in Ihre Unterhaltung einfügen möchten.

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
