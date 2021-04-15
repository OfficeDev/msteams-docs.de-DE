---
title: Entwerfen Ihrer Messagingerweiterung
description: Erfahren Sie, wie Sie eine Microsoft Teams-Messagingerweiterung entwerfen und das Microsoft Teams UI Kit erhalten.
keywords: Bewährte Methode für Teams-Entwurfsrichtlinien zur Referenz von Messagingerweiterungen
author: heath-hamilton
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: c616d8e3e7c40ae124f96cb80a42873f9aaa7865
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51697011"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Entwerfen Ihrer Microsoft Teams-Messagingerweiterung

Messagingerweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln in einer Nachricht, ohne aus der Unterhaltung zu navigieren.
Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Messagingerweiterungen in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Im Microsoft Teams UI Kit finden Sie umfassende Entwurfsrichtlinien für Messagingerweiterungen, einschließlich Elementen, die Sie bei Bedarf packen und ändern können.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Hinzufügen einer Messagingerweiterung

Sie können eine Messagingerweiterung in den folgenden Teams-Kontexten hinzufügen:

* Aus dem Teams Store (AppSource).
* In einem Kanal, Chat oder einer Besprechung (vor, während und nach) in der Nähe des Verfassenfelds. Es ist erwähnenswert, wenn Sie eine Messagingerweiterung an einem dieser Orte hinzufügen, nur Sie können sie in diesem Kontext verwenden.

Das folgende Beispiel zeigt, wie Sie eine Messagingerweiterung in einem Kanal hinzufügen.

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung in der Nähe des Verfassenfelds in einem Kanal hinzufügen." border="false":::

## <a name="set-up-a-messaging-extension"></a>Einrichten einer Messagingerweiterung

Die Authentifizierung ist nicht zwingend erforderlich, aber wenn Ihre App so etwas wie ein Ticketverfolgungstool ist, müssen Sie sich möglicherweise anmelden, um die Messagingerweiterung zu verwenden.

Aus Gründen der Konsistenz in teams-Apps können Sie den Anmeldebildschirm nicht anpassen. Wenn Sie die einmalige Anmeldung (Single Sign-On, SSO)-Authentifizierung verwenden, werden Benutzer automatisch angemeldet.

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Beispiel zeigt den Setupbildschirm der Messagingerweiterung mit einer Anmeldeschaltfläche." border="false":::

## <a name="types-of-messaging-extensions"></a>Arten von Messagingerweiterungen

Messagingerweiterungen können Suchbefehle, Aktionsbefehle oder beides enthalten. Ihre Befehle hängen von den Features Ihrer App ab und davon, wie diese in Teams passen.

### <a name="search-commands"></a>Suchbefehle

Mithilfe von Suchbefehlen können Benutzer Ihre Messagingerweiterung verwenden, um schnell externe Inhalte zu finden und in eine Nachricht zu einfügen. Suchbefehle werden häufig im Verfassenfeld verfügbar gemacht. Sie können beispielsweise eine Diskussion starten oder einer Diskussion hinzufügen, indem Sie einen Teil des Inhalts freigeben – ohne Teams jemals zu verlassen.

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Beispiel zeigt eine suchbasierte Messagingerweiterung, die über das Verfassenfeld gestartet wird." border="false":::

#### <a name="compose-box-layout-options"></a>Layoutoptionen für Verfassen von Schachteln

Sie haben einige Optionen zum Anzeigen von Suchergebnissen der Messagingerweiterung, einschließlich [Listen- und Rasteransichten.](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests)

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Abbildungen mit Layoutoptionen für Suchergebnisse für Messagingerweiterungen." border="false":::

### <a name="action-commands"></a>Aktionsbefehle

Mit Aktionsbefehlen können Benutzer Aktionen auslösen und Anforderungen in externen Diensten in Teams verarbeiten. Wenn Ihre App beispielsweise Bestellungen verfolgt, kann ein Benutzer eine neue Bestellung erstellen, indem er den Inhalt der Nachricht eines Kollegen direkt in seinem Chat verwendet.

Für aktionsbasierte Messagingerweiterungen müssen Benutzer häufig ein Formular oder eine andere Art von Konfiguration innerhalb eines modalen Formulars abschließen. Sie können diese Erfahrungen mit [Aufgabenmodulen erstellen.](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)

## <a name="open-a-messaging-extension"></a>Öffnen einer Messagingerweiterung

Das Verfassenfeld und Nachrichten/Beiträge sind die primären Kontexte, in denen Personen Messagingerweiterungen verwenden.

### <a name="from-the-compose-box"></a>Aus dem Verfassenfeld

Nach dem Hinzufügen können Benutzer Ihre Messagingerweiterung öffnen, indem sie ihr App-Symbol unterhalb des Verfassenfelds auswählen. In diesem Beispiel verfügt die Erweiterung über Such- und Aktionsbefehle.

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung aus dem Verfassenfeld öffnen." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a>Aus einer Chatnachricht oder einem Kanalbeitrag

Nach dem Hinzufügen können Benutzer das Symbol **Mehr** in der Chatnachricht oder dem Kanalbeitrag auswählen, um die :::image type="icon" source="../../assets/icons/teams-client-more.png"::: Aktionsbefehle Ihrer Erweiterung zu finden. Ihre Erweiterung kann unter **Weitere Aktionen basierend auf der** Verwendung aufgeführt werden.

> [!NOTE]
> Unterstützung für weitere Aktionen aus einer Chatnachricht oder einem Kanalbeitrag ist auf der mobilen Microsoft Teams-Plattform nicht verfügbar. 

#### <a name="chat-message"></a>Chatnachricht

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung aus einer Chatnachricht öffnen." border="false":::

#### <a name="channel-post"></a>Kanalbeitrag

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Beispiel zeigt, wie Sie eine Messagingerweiterung über einen Kanalbeitrag öffnen." border="false":::

## <a name="use-a-messaging-extension"></a>Verwenden einer Messagingerweiterung

In den folgenden Szenarien wird die primäre Verwendung von Messagingerweiterungen für Personen gezeigt.

### <a name="insert-content-into-a-message"></a>Einfügen von Inhalten in eine Nachricht

**1. Wählen Sie eine Messagingerweiterung aus.** Benutzer können im Verfassenfeld nach den Inhalten suchen, die sie freigeben möchten.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Beispiel zeigt einen Benutzer, der nach Inhalt sucht, der aus dem Verfassenfeld eingefügt werden soll." border="false":::

**2. Einfügen von Inhalten**. Nachdem sie veröffentlicht wurden, können andere Personen den Inhalt beantworten oder auswählen, um weitere Informationen in Ihrer App anzuzeigen.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Beispiel zeigt einen Benutzer, der Inhalte in einer Kanal unterhaltung postet." border="false":::

### <a name="take-action-on-a-message"></a>Ergreifen von Aktionen für eine Nachricht

**1. Wählen Sie eine Messagingerweiterung aus.** Ihre App kann einen oder mehrere Aktionsbefehle enthalten.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Beispiel zeigt einen Benutzer, der einen Befehl für die Messagingerweiterungsaktion aus wählt." border="false":::

**2. Führen Sie die Aktion aus.** Ihre App kann alle von der Nachrichtenaktion gesendeten Inhalte oder Daten empfangen und verarbeiten. Dies ermöglicht Benutzern, in ihrer Unterhaltung zu bleiben und sich im folgenden Beispiel keine Gedanken über die direkte Eingabe von Informationen in Ihrer App zu machen.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel zum Ergreifen von Aktionen für eine Nachricht." border="false":::

### <a name="preview-links"></a>Vorschaulinks

Mit Messagingerweiterungen können Sie auch rich links from a recognized URL in eine Nachricht einfügen (diese Funktion wird als [Link unfurling bezeichnet.)](../../messaging-extensions/how-to/link-unfurling.md)

**1. Fügen Sie einen erkannten Link** in das Verfassenfeld ein.

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Ein Beispiel zeigt einen Benutzer, der einen Link in das Kompostfeld einklinkt." border="false":::

**2. Einfügen von Inhalten**. Wenn Ihre App die URL im Verfassenfeld erkennt, wird der Link als Karte gerendert, die eine inhaltsreiche Vorschau des Webinhalts bietet. (Weitere Informationen finden Sie unter [Entwurfsrichtlinien für](../../task-modules-and-cards/cards/design-effective-cards.md) adaptive Karten.)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Beispiel zeigt, wie die URL, da sie von Ihrer App erkannt wird, einige umfangreiche Inhalte im Verfassenfeld enthält." border="false":::

## <a name="manage-a-messaging-extension"></a>Verwalten einer Messagingerweiterung

Durch klicken mit der rechten Maustaste auf Ihr Symbol können Benutzer Ihre Messagingerweiterung anheften, entfernen oder konfigurieren.

## <a name="anatomy"></a>Anatomie

### <a name="messaging-extension-in-the-compose-box"></a>Messagingerweiterung im Verfassenfeld

Das folgende Beispiel ist eine Messagingerweiterung, die über das Verfassenfeld geöffnet wird.

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung der Anatomie der Benutzeroberfläche einer Messagingerweiterung im Verfassenfeld." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo:** Farbsymbol Ihres App-Logos.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Menüsymbol für Aktionsbefehle (optional):** Öffnet eine Liste der Aktionsbefehle für Ihre Messagingerweiterung (sofern vorhanden).
|4 |**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.|
|5 |**Registerkartenmenü (optional):** Stellt mehrere Inhaltskategorien zur Auswahl.|
|6 |**Menü "Aktionsbefehle" (optional):** Zeigt eine Liste der Aktionsbefehle an (wenn Sie einen angeben).|
|7 |**App-Inhalt**: In erster Linie zum Anzeigen von Suchergebnissen. Im folgenden Beispiel wird das Listenlayout verwendet (rasterlayout ist eine weitere Option).|
|8 |**App-Logo:** Gliederungssymbol Ihres App-Logos.|

### <a name="messaging-extension-management-menu"></a>Menü "Verwaltung von Nachrichtenerweiterungen"

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung der Benutzeroberflächenanatomie eines Menüs zur Verwaltung von Messagingerweiterungen." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Unpin**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.|
|2|**Remove**: Entfernt die Messagingerweiterung aus dem Kanal, Chat oder der Besprechung.|

## <a name="best-practices"></a>Bewährte Methoden

### <a name="setup-and-general-usage"></a>Setup und allgemeine Verwendung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel zur Einrichtung und allgemeinen Verwendung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Do: Integration in einmaliges Anmelden

SSO erleichtert, schneller und sicherer den Anmeldevorgang. Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich auch nicht erneut anmelden, um auf die Messagingerweiterung zu zugreifen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für die Integration mit einmaligem Anmelden." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Don't: Take users away from the conversation

Messagingerweiterungen sind Verknüpfungen, die den Kontextwechsel reduzieren sollen. Ihre Erweiterung sollte z. B. Benutzer nicht an eine Webseite außerhalb von Teams weiterverdingen.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Do: Highlight your messaging extension

Messagingerweiterungen sind nicht immer einfach zu finden. Fügen Sie Screenshots dazu hinzu, wie Sie sie auf der Seite mit den App-Details verwenden. Wenn Ihre App auch einen Bot enthält, können Sie die Hilfedokumentation zur Messagingerweiterung in eine Bot-Willkommenstour einfüllen.

### <a name="templating"></a>Templating

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für templating." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Do: Lassen Sie Teams einen Teil der Entwurfsarbeit nach Möglichkeit behandeln

Wenn es für Ihre Verwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messagingerweiterung erstellen. Teams rendert diese Arten von Erweiterungen mit integriertem Theming und Barrierefreiheit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für die Verarbeitung von Entwurfsarbeiten." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Don't: Embed your entire app in a task module

Wenn ihre Messagingerweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul einfach und zeigen Sie nur die Komponenten an, die zum Ausführen der Aktion erforderlich sind.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für das Thema." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Do: Nutzen von Teams-Farbtoken

Jedes Teams-Design verfügt über ein eigenes Farbschema. Verwenden Sie Farbtoken <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">(Fluent UI)</a> in Ihrem Entwurf, um Designänderungen automatisch zu verarbeiten.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für Farbtoken." border="false":::

#### <a name="dont-hard-code-color-values"></a>Don't: Hartcodefarbwerte

Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und brauchen mehr Zeit für die Verwaltung.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für Aktionen." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Do: Fügen Sie Aktionsbefehle ein, die im Kontext sinnvoll sind

Nachrichtenaktionen sollten sich darauf beziehen, was ein Benutzer anschaut. Stellen Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder einer Arbeitsaufgabe mithilfe des Texts in einem Beitrag einer Person zur Verfügung.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für Aktionsbefehle." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Don't: Include actions commands that aren't contextual

Eine Nachrichtenaktion zum **Anzeigen Des Dashboards** scheint wahrscheinlich nicht mit den meisten Unterhaltungen verbunden zu sein.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Suchen

#### <a name="do-show-search-results-while-typing"></a>Do: Anzeigen von Suchergebnissen während der Eingabe

Geben Sie vorgeschlagene Suchergebnisse an, während Benutzer eingeben. Möglicherweise finden sie die benötigten Inhalte schneller mit minimaler Zeichenmenge.

#### <a name="dont-require-users-to-submit-a-query"></a>Don't: Benutzer zum Senden einer Abfrage benötigen

Sie können benutzer eine Taste drücken oder eine Schaltfläche auswählen, um Abfragen an Ihre App zu senden. Während dies im App-Dienste-Dienst möglicherweise einfacher ist, sind die Personen möglicherweise verwirrt, dass bei der Eingabe keine Echtzeitsuchergebnisse angezeigt werden.

#### <a name="do-consider-zero-term-queries"></a>Do: Berücksichtigen von Zero-Term-Abfragen

Bevor ein Benutzer beispielsweise etwas in das Suchfeld schreibt, zeigen Sie an, was er zuletzt in Ihrer App angezeigt hat. Es ist möglich, dass sie diese Inhalte in ihre Unterhaltung einfügen möchten.

## <a name="validate-your-design"></a>Validieren Ihres Designs

Wenn Sie Ihre App in AppSource veröffentlichen möchten, sollten Sie die Entwurfsprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Richtlinien zur Designvalidierung](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
