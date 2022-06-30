---
title: Gestalten Ihrer Nachrichtenerweiterung
description: Erfahren Sie, wie Sie eine Teams-Nachrichtenerweiterung entwerfen und das Microsoft Teams-UI-Kit erhalten. Beschreibt Teams-Gestaltungsrichtlinien für Nachrichtenerweiterungen – Tipps Best Praxis
author: heath-hamilton
ms.localizationpriority: high
ms.author: surbhigupta
ms.topic: conceptual
ms.openlocfilehash: 2d3d31a0e59be22eb4f84bbdeb70897f4d584b83
ms.sourcegitcommit: c398dfdae9ed96f12e1401ac7c8d0228ff9c0a2b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2022
ms.locfileid: "66558751"
---
# <a name="designing-your-microsoft-teams-message-extension"></a>Entwerfen Ihrer Microsoft Teams-Nachrichtenerweiterung

Nachrichtenerweiterungen sind Abkürzungen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne die Konversation verlassen zu müssen.
Die folgenden Informationen beschreiben und veranschaulichen, wie Personen in Teams Nachrichtenerweiterungen hinzufügen, verwenden und verwalten können, und dienen als Leitfaden für Ihr App-Design.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-Benutzeroberflächenbausatz

Umfassende Richtlinien für das Design von Nachrichtenerweiterungen, einschließlich Elementen, die Sie bei Bedarf übernehmen und ändern können, finden Sie im Microsoft Teams UI-Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich den Microsoft Teams-Benutzeroberflächenbausatz (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-message-extension"></a>Hinzufügen einer Nachrichtenerweiterung

Sie können eine Nachrichtenerweiterung in den folgenden Teams-Kontexten hinzufügen:

* Aus dem Teams-Store.
* In einem Kanal, Chat oder einer Besprechung (vor, während und nachher) in der Nähe des "Verfassen"-Felds. Beachten Sie, wenn Sie eine Nachrichtenerweiterung an einer dieser Stellen hinzufügen, können nur Sie sie in diesem Kontext verwenden.

Die folgenden Beispiele zeigen, wie Sie eine Nachrichtenerweiterung in einem Kanal hinzufügen.

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/messaging-extension/mobile-add-in-channel.png" alt-text="Das Beispiel zeigt, wie Sie eine Nachrichtenerweiterung in der Nähe des Felds „Verfassen“ in einem Kanal auf Mobilgeräten hinzufügen.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Das Beispiel zeigt, wie Sie eine Nachrichtenerweiterung in der Nähe des Felds „Verfassen“ in einem Kanal hinzufügen.":::

## <a name="set-up-a-message-extension"></a>Einrichten einer Nachrichtenerweiterung

Eine Authentifizierung ist nicht zwingend erforderlich, aber wenn es sich bei Ihrer Anwendung um ein Tool zur Nachverfolgung von Tickets handelt, müssen sich die Benutzer möglicherweise anmelden, um die Nachrichtenerweiterung nutzen zu können.

Aus Gründen der Konsistenz zwischen Teams-Apps können Sie den Anmeldebildschirm nicht anpassen. Wenn Sie die Authentifizierung mit einmaligem Anmelden (Single Sign-On, SSO) verwenden, werden Benutzer automatisch angemeldet.

### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-set-up.png" alt-text="Das Beispiel zeigt den Einrichtungsbildschirm der Nachrichtenerweiterung mit einer Anmeldeschaltfläche auf dem Handy.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Das Beispiel zeigt den Einrichtungsbildschirm für Nachrichtenerweiterungen mit einer Anmeldeschaltfläche.":::

## <a name="types-of-message-extensions"></a>Arten von Nachrichtenerweiterungen

Nachrichtenerweiterungen können Suchbefehle, Aktionsbefehle oder beides beeinhalten. Ihre Befehle hängen von den Features Ihrer App und davon ab, wie diese in Teams-Anwendungsfälle passen.

### <a name="search-commands"></a>Suchbefehle

Mit Suchbefehlen können Personen Ihre Nachrichtenerweiterung nutzen, um schnell externe Inhalte zu finden und in eine Nachricht einzufügen. Suchbefehle werden häufig im "Verfassen"-Feld zur Verfügung gestellt. Sie können z. B. eine Diskussion beginnen oder etwas zu einer Diskussion hinzufügen, indem Sie einen Teil des Inhalts teilen – ohne Teams verlassen zu müssen.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Nachrichtenerweiterung, die über das Erstellungsfeld auf dem Handy gestartet wird.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Nachrichtenerweiterung, die über das Erstellungsfeld gestartet wird.":::

#### <a name="compose-box-layout-options"></a>Layoutoptionen für das "Verfassen"-Feld 

Sie haben einige Optionen für die Anzeige der Suchergebnisse von Nachrichtenerweiterungen, darunter [Listen- und Gitteransichten](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Illustrationen mit Layoutoptionen für Suchergebnisse der Nachrichtenerweiterung.":::

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle ermöglichen es Personen, Aktionen auszulösen und Anforderungen in externen Diensten in Teams zu verarbeiten. Wenn Ihre App beispielsweise Bestellungen nachverfolgt, kann ein Benutzer eine neue Bestellung erstellen, indem er den Inhalt der Nachricht eines Kollegen direkt in seinem Chat verwendet.

Bei aktionsbasierten Nachrichtenerweiterungen müssen Benutzer häufig ein Formular oder eine andere Art von Konfiguration innerhalb eines Modals ausfüllen. Sie können diese Erfahrungen mit [Aufgabenmodulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.

## <a name="open-a-message-extension"></a>Öffnen einer Nachrichtenerweiterung

Das Feld „Verfassen“ und Nachrichten oder Beiträge sind die primären Kontexte, in denen Personen Nachrichtenerweiterungen verwenden.

### <a name="from-the-compose-box"></a>Über das "Verfassen"-Feld

Nach dem Hinzufügen können Benutzer Ihre Nachrichtenerweiterung öffnen, indem sie ihr App-Symbol unter dem Feld „Verfassen“ auswählen. In diesen Beispielen verfügt die Erweiterung über Such- und Aktionsbefehle.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Nachrichtenerweiterung über das Feld „Verfassen“ auf Mobilgeräten öffnen.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie eine Nachrichtenerweiterung über das Feld „Verfassen“ geöffnet wird.":::

### <a name="from-a-chat-message-or-channel-post"></a>Aus einer Chatnachricht oder einem Kanalbeitrag

Nach dem Hinzufügen können Benutzer das Symbol **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chatnachricht oder im Kanalbeitrag auswählen, um die Aktionsbefehle Ihrer Erweiterung zu finden. Ihre Erweiterung wird möglicherweise basierend auf der Nutzung unter **Weitere Aktionen** aufgeführt.

#### <a name="chat-message"></a>Chatnachricht

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Das Beispiel zeigt, wie eine Nachrichtenerweiterung aus einer Chatnachricht geöffnet wird.":::

#### <a name="channel-post"></a>Kanalbeitrag

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Das Beispiel zeigt, wie Sie eine Nachrichtenerweiterung über einen Kanalbeitrag auf mobilen Geräten öffnen.":::

## <a name="use-a-message-extension"></a>Verwenden einer Nachrichtenerweiterung

In den folgenden Szenarien werden die wichtigsten Verwendungsmöglichkeiten von Nachrichtenerweiterungen veranschaulicht.

### <a name="insert-content-into-a-message"></a>Einfügen von Inhalt in eine Nachricht

**1. Wählen Sie eine Nachrichtenerweiterung** aus. Benutzer können über das Feld „Verfassen“ nach dem Inhalt suchen, den sie freigeben möchten.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der auf einem Mobilgerät über das &quot;Verfassen&quot;-Feld nach Inhalten sucht, die eingefügt werden sollen.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der nach Inhalten sucht, die aus dem &quot;Verfassen&quot;-Feld eingefügt werden sollen.":::

**2. Inhalt einfügen**. Nach der Veröffentlichung können andere Personen auf den Inhalt antworten oder diesen auswählen, um weitere Informationen in Ihrer App anzuzeigen.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-posted.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät Inhalte in einer Kanalunterhaltung postet.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Das Beispiel zeigt, wie ein Benutzer Inhalte in einer Kanalunterhaltung postet.":::

### <a name="take-action-on-a-message"></a>Aktionen für eine Nachricht ausführen

**1. Wählen Sie eine Nachrichtenerweiterung** aus. Ihre App kann einen oder mehrere Aktionsbefehle enthalten.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Aktionsbefehl für die Nachrichtenerweiterung auswählt.":::

**2. Führen Sie die Aktion aus**. Ihre App kann alle Inhalte oder Daten empfangen und verarbeiten, die von der Nachrichtenaktion gesendet werden. Benutzer führen die Aktion in Ihrer App aus, während sie in ihrer Unterhaltung bleiben.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel für das Ausführen von Aktionen für eine Nachricht.":::

### <a name="preview-links"></a>Vorschaulinks

Mit Nachrichtenerweiterungen können Sie auch Rich-Links von einer erkannten URL in eine Nachricht einfügen (diese Funktion wird als [Linkentfaltung bezeichnet](../../messaging-extensions/how-to/link-unfurling.md)).

**1. Fügen Sie einen erkannten Link** in das "Verfassen"-Feld ein.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät einen Link in das &quot;Verfassen&quot;-Feld eingibt.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Link in das &quot;Verfassen&quot;-Feld eingibt.":::

**2. Inhalt einfügen**. Wenn Ihre Anwendung die URL im Erfassungsfeld erkennt, wird der Link als Karte dargestellt, die eine umfassende Vorschau des Webinhalts bietet. (Weitere Informationen finden Sie in den [Designrichtlinien für adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md)).

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL auf einem Mobilgerät umfangreiche Inhalte in das &quot;Verfassen&quot;-Feld einschließt, da sie von Ihrer App erkannt wird.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL umfangreiche Inhalte in das &quot;Verfassen&quot;-Feld einschließt, da sie von Ihrer App erkannt wird.":::

## <a name="manage-a-message-extension"></a>Verwalten einer Nachrichtenerweiterung

Wenn sie mit der rechten Maustaste auf Ihr Symbol klicken, können Benutzer Ihre Nachrichtenerweiterung anheften, entfernen oder konfigurieren.

## <a name="anatomy"></a>Anatomie

### <a name="message-extension-in-the-compose-box"></a>Nachrichtenerweiterung im Feld „Verfassen“

Die folgenden Beispiele zeigen eine Nachrichtenerweiterung, die über das Feld „Verfassen“ geöffnet wurde.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/messaging-extension/mobile-anatomy-compose.png" alt-text="Illustration der UI-Anatomie einer Nachrichtenerweiterung im Erstellungsfeld auf einem Mobilgerät.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Name**: Vollständiger Name Ihrer App.|
|2|**Menüsymbol für Aktionsbefehle (optional)**: Öffnet eine Liste von Aktionsbefehlen für Ihre Nachrichtenerweiterung (sofern vorhanden).
|3|**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.|
|4|**Registerkartenmenü (optional)**: Stellt mehrere Inhaltskategorien bereit.|
|5|**Menü "Aktionsbefehle" (optional)**: Zeigt die Liste der Aktionsbefehle an (sofern angegeben).|
|6 |**App-Inhalt**: Hauptsächlich zum Anzeigen von Suchergebnissen.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung, die die UI-Anatomie einer Nachrichtenerweiterung im Feld „Verfassen“ zeigt.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo**: Farbsymbol Ihres App-Logos.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Menüsymbol für Aktionsbefehle (optional)**: Öffnet eine Liste von Aktionsbefehlen für Ihre Nachrichtenerweiterung (sofern vorhanden).
|4|**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.|
|5|**Registerkartenmenü (optional)**: Stellt mehrere Inhaltskategorien bereit.|
|6 |**Menü "Aktionsbefehle" (optional)**: Zeigt die Liste der Aktionsbefehle an (sofern angegeben).|
|7 |**App-Inhalt**: Hauptsächlich zum Anzeigen von Suchergebnissen. Im folgenden Beispiel wird das Listenlayout verwendet (Rasterlayout ist eine weitere Option).|
|8 |**App-Logo**: Gliederungssymbol Ihres App-Logos.|

### <a name="message-extension-management-menu"></a>Menü „Verwalten von Nachrichtenerweiterungen“

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung der UI-Struktur eines Menüs für die Verwaltung von Nachrichtenerweiterungen.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Lösen sie**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.|
|2|**Entfernen**: Entfernt die Nachrichtenerweiterung aus dem Kanal, Chat oder der Besprechung.|

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="setup-and-general-usage"></a>Setup und allgemeine Nutzung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel für Setup und allgemeine Nutzung.":::

#### <a name="do-integrate-with-single-sign-on"></a>Was Sie tun sollten: Integration mit einmaligem Anmelden

SSO macht den Anmeldeprozess einfacher, schneller und sicherer. Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich nicht noch einmal anmelden, um auf die Nachrichtenerweiterung zuzugreifen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für die Integration mit einmaligem Anmelden.":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Was Sie nicht tun sollten: Benutzer aus der Unterhaltung entfernen

Nachrichtenerweiterungen sind Abkürzungen, die den Kontextwechsel reduzieren sollen. Ihre Erweiterung sollte Benutzer beispielsweise nicht zu einer Webseite außerhalb von Teams weiterleiten.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-message-extension"></a>Do: Nachrichtenerweiterung hervorheben

Nachrichtenerweiterungen sind nicht immer leicht zu finden. Fügen Sie Screenshots zur Verwendungsweise auf der Detailseite Ihrer App ein. Wenn Ihre Anwendung auch einen Bot enthält, können Sie die Hilfedokumentation zur Nachrichtenerweiterung in eine Bot-Begrüßungstour einbinden.

### <a name="templating"></a>Vorlagen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für Vorlagen.":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Was Sie tun sollten: Lassen Sie Teams nach Möglichkeit einen Teil der Entwurfsarbeit erledigen

Wenn es für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Nachrichtenerweiterung erstellen. Teams rendert diese Arten von Erweiterungen mit integriertem Design und Barrierefreiheit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für die Verarbeitung von Entwurfsarbeiten.":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Was Sie nicht tun sollten: Einbetten der gesamten App in ein Aufgabenmodul

Wenn Ihre Nachrichtenerweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul einfach, und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Design

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für Design.":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Was Sie tun sollten: Teams-Farbtoken nutzen

Jedes Teams-Design verfügt über ein eigenes Farbschema. Um Designänderungen automatisch zu verarbeiten, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für Farbtoken.":::

#### <a name="dont-hard-code-color-values"></a>Was Sie nicht tun sollten: Hartcodieren von Farbwerten

Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit für die Verwaltung.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für Aktionen.":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Was Sie tun sollten: Aktionsbefehle einschließen, die im Kontext sinnvoll sind

Nachrichtenaktionen sollten sich auf das beziehen, was ein Benutzer sieht. Geben Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder Arbeitselements mithilfe des Texts in einem Beitrag einer Person an.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für Aktionsbefehle.":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Was Sie nicht tun sollten: Aktionsbefehle einschließen, die nicht kontextbezogen sind

Eine Nachrichtenaktion zum **Anzeigen Ihres Dashboards** scheint wahrscheinlich von den meisten Unterhaltungen getrennt zu sein.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Suchvorgänge

#### <a name="do-show-search-results-while-typing"></a>Was Sie tun sollten: Suchergebnisse während der Eingabe anzeigen

Geben Sie vorgeschlagene Suchergebnisse an, während Benutzer Text eingeben. Möglicherweise finden sie so den benötigten Inhalt schneller mit einer minimalen Anzahl von Zeichen.

#### <a name="dont-require-users-to-submit-a-query"></a>Was Sie nicht tun sollten: Benutzer müssen eine Abfrage übermitteln

Sie können festlegen, dass Benutzer eine Taste drücken oder eine Schaltfläche auswählen, um Abfragen an Ihre App zu senden. Obwohl dies für Ihren App-Services-Dienst einfacher sein kann, sind Benutzer möglicherweise verwirrt, dass sie während der Texteingabe keine Echtzeitsuchergebnisse sehen.

#### <a name="do-consider-zero-term-queries"></a>Was Sie tun sollten: Erwägen Sie Nullausdrucksabfragen

Bevor ein Benutzer beispielsweise etwas in das Suchfeld schreibt, zeigen Sie an, was er zuletzt in Ihrer App angesehen hat. Es ist möglich, dass sie diesen Inhalt in ihre Unterhaltung einfügen möchten.
