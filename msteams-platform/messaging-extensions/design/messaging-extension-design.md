---
title: Entwerfen Ihrer Messagingerweiterung
description: Erfahren Sie, wie Sie eine Teams Messaging-Erweiterung entwerfen und das Microsoft Teams UI Kit abrufen.
keywords: Teams entwerfen Richtlinien referenzieren Messaging-Erweiterungen Tipps best Practice
author: heath-hamilton
localization_priority: Normal
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ed1f0f2eb2ce8d429a8a780bd2c4c4eb421d6d54
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566215"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Entwerfen ihrer Microsoft Teams Messaging-Erweiterung

Messagingerweiterungen sind Verknüpfungen zum Einfügen von App-Inhalten oder zum Handeln auf eine Nachricht, ohne von der Unterhaltung weg zu navigieren.
Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Messagingerweiterungen in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Richtlinien für den Entwurf von Messagingerweiterungen, einschließlich Elementen, die Sie bei Bedarf aussuchen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Hinzufügen einer Messagingerweiterung

Sie können eine Messagingerweiterung in den folgenden Teams Kontexten hinzufügen:

* Aus dem Teams Store (AppSource).
* In einem Kanal, Chat oder Meeting (vorher, während und nach) in der Nähe des Verfassensfeldes. Es ist erwähnenswert, wenn Sie eine Messaging-Erweiterung an einem dieser Orte hinzufügen, nur Sie können es in diesem Kontext verwenden.

Das folgende Beispiel zeigt, wie Sie eine Messagingerweiterung in einem Kanal hinzufügen:

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Ein Beispiel zeigt, wie Sie eine Messagingerweiterung in der Nähe des Verfassensfeldes in einem Kanal hinzufügen." border="false":::

## <a name="set-up-a-messaging-extension"></a>Einrichten einer Messagingerweiterung

Die Authentifizierung ist nicht obligatorisch, aber wenn Ihre App so etwas wie ein Ticketverfolgungstool ist, müssen sich möglicherweise Personen anmelden, um die Messagingerweiterung verwenden zu können.

Aus Gründen der Konsistenz in Teams Apps können Sie den Anmeldebildschirm nicht anpassen. Wenn Sie die SSO-Authentifizierung (Single Sign-On) verwenden, werden Benutzer automatisch angemeldet.

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Das Beispiel zeigt den Setupbildschirm für die Messagingerweiterung mit einer Anmeldeschaltfläche." border="false":::

## <a name="types-of-messaging-extensions"></a>Arten von Messagingerweiterungen

Messagingerweiterungen können Suchbefehle, Aktionsbefehle oder beides haben. Ihre Befehle hängen von den Funktionen Ihrer App ab und davon, wie diese in Teams Anwendungsfälle passen.

### <a name="search-commands"></a>Suchbefehle

Mit Suchbefehlen können Benutzer Ihre Messaging-Erweiterung verwenden, um externe Inhalte schnell zu finden und in eine Nachricht einzufügen. Suchbefehle werden häufig im Feld Verfassen zur Verfügung gestellt. Sie können z. B. eine Diskussion starten oder hinzufügen, indem Sie einen Inhalt freigeben, ohne jemals Teams zu verlassen.

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Messagingerweiterung, die aus dem Verfassenfeld gestartet wurde." border="false":::

#### <a name="compose-box-layout-options"></a>Layoutoptionen des Felds verfassen

Sie haben einige Optionen zum Anzeigen von Suchergebnissen für Messagingerweiterungen, einschließlich [Listen- und Rasteransichten](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Abbildungen mit Layoutoptionen für Suchergebnisse für Messagingerweiterungen." border="false":::

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle ermöglichen es Benutzern, Aktionen auszulösen und Anforderungen in externen Diensten innerhalb Teams zu verarbeiten. Wenn Ihre App beispielsweise Bestellungen nachverfolgt, kann ein Benutzer eine neue Bestellung mithilfe des Inhalts der Nachricht eines Kollegen direkt in seinem Chat erstellen.

Aktionsbasierte Messagingerweiterungen erfordern häufig, dass Benutzer ein Formular oder eine andere Art von Konfiguration innerhalb eines Modals ausfüllen. Sie können diese Erfahrungen mit [Aufgabenmodulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.

## <a name="open-a-messaging-extension"></a>Öffnen einer Messagingerweiterung

Das Verfassen-Feld und Nachrichten oder Beiträge sind die primären Kontexte, in denen Benutzer Messagingerweiterungen verwenden.

### <a name="from-the-compose-box"></a>Aus der Verfassenbox

Nach dem Zusatz können Benutzer Ihre Messagingerweiterung öffnen, indem sie Ihr App-Symbol unter dem Verfassen-Feld auswählen. In diesem Beispiel verfügt die Erweiterung über Such- und Aktionsbefehle:

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Messagingerweiterung aus dem Verfassen-Feld öffnen." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a>Von einer Chat-Nachricht oder einem Kanalbeitrag

Nach dem Zusatz können Benutzer das Symbol **Mehr** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chat-Nachricht oder im Kanalbeitrag auswählen, um die Aktionsbefehle Ihrer Erweiterung zu finden. Ihre Erweiterung kann unter **Weitere Aktionen** basierend auf der Nutzung aufgeführt werden.

> [!NOTE]
> Unterstützung für weitere Aktionen von einer Chat-Nachricht oder einem Kanalbeitrag ist auf Microsoft Teams mobilen Plattform nicht verfügbar. 

#### <a name="chat-message"></a>Chatnachricht

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Ein Beispiel zeigt, wie sie eine Messagingerweiterung aus einer Chatnachricht öffnen." border="false":::

#### <a name="channel-post"></a>Channel-Post

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Ein Beispiel zeigt, wie sie eine Messagingerweiterung über einen Kanalbeitrag öffnen." border="false":::

## <a name="use-a-messaging-extension"></a>Verwenden einer Messagingerweiterung

Die folgenden Szenarien zeigen die primäre Verwendung von Messagingerweiterungen.

### <a name="insert-content-into-a-message"></a>Einfügen von Inhalten in eine Nachricht

**1. Wählen Sie eine Messaging-Erweiterung**. Benutzer können im Verfassen-Feld nach dem Inhalt suchen, den sie freigeben möchten.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der nach Inhalten sucht, die aus dem Verfassenfeld eingefügt werden sollen." border="false":::

**2. Fügen Sie Inhalt** ein. Nach der Veröffentlichung können andere Personen antworten oder den Inhalt auswählen, um weitere Informationen in Ihrer App anzuzeigen.

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Ein Beispiel zeigt einen Benutzer, der Inhalte in einer Kanalunterhaltung postet." border="false":::

### <a name="take-action-on-a-message"></a>Maßnahmen für eine Nachricht

**1. Wählen Sie eine Messaging-Erweiterung**. Ihre App kann einen oder mehrere Aktionsbefehle enthalten.

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Aktionsbefehl für die Messagingerweiterung auswählt." border="false":::

**2. Schließen Sie die Aktion ab.** Ihre App kann alle Inhalte oder Daten empfangen und verarbeiten, die von der Nachrichtenaktion gesendet werden. Auf diese Weise können Benutzer in ihrer Unterhaltung bleiben und sich im folgenden Beispiel keine Gedanken über die direkte Eingabe von Informationen in Ihrer App machen.

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel, wie Sie Maßnahmen für eine Nachricht ergreifen." border="false":::

### <a name="preview-links"></a>Vorschaulinks

Messagingerweiterungen ermöglichen es Ihnen auch, Rich Links von einer erkannten URL in eine Nachricht einzufügen (diese Funktion wird als [Link-Entfurling](../../messaging-extensions/how-to/link-unfurling.md)bezeichnet.)

**1. Fügen Sie einen erkannten Link** in das Verfassen-Feld ein.

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Link in das Kompostfeld einfügt." border="false":::

**2. Fügen Sie Inhalt** ein. Wenn Ihre App die URL im Verfassen-Feld erkennt, wird der Link als Karte gerendert, die eine inhaltsreiche Vorschau des Webinhalts bietet. (Weitere Informationen finden Sie unter [Designrichtlinien für Adaptive Karten.)](../../task-modules-and-cards/cards/design-effective-cards.md)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL, da sie von Ihrer App erkannt wird, einige umfangreiche Inhalte in das Verfassen-Feld enthält." border="false":::

## <a name="manage-a-messaging-extension"></a>Verwalten einer Messagingerweiterung

Wenn Sie mit der rechten Maustaste auf Ihr Symbol klicken, können Benutzer Ihre Messagingerweiterung anheften, entfernen oder konfigurieren.

## <a name="anatomy"></a>Anatomie

### <a name="messaging-extension-in-the-compose-box"></a>Messagingerweiterung im Verfassenfeld

Das folgende Beispiel ist eine Messagingerweiterung, die aus dem Verfassen-Feld geöffnet wird.

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung, die die Ui-Anatomie einer Messagingerweiterung im Verfassen-Feld zeigt." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo**: Farbsymbol Ihres App-Logos.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Aktionsbefehls-Menüsymbol (optional):** Öffnet eine Liste von Aktionsbefehlen für Ihre Messagingerweiterung (falls vorhanden).
|4 |**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.|
|5 |**Tab-Menü (optional):** Bietet mehrere Inhaltskategorien.|
|6 |**Aktionsbefehlsmenü (optional)**: Zeigt eine Liste der Aktionsbefehle an (falls Sie irgendwelche angeben).|
|7 |**App-Inhalt**: In erster Linie zum Anzeigen von Suchergebnissen. Das Beispiel hier ist die Verwendung des Listenlayouts (Rasterlayout ist eine andere Option).|
|8 |**App-Logo**: Gliederungssymbol Ihres App-Logos.|

### <a name="messaging-extension-management-menu"></a>Messagingerweiterungsverwaltungsmenü

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung, die die Ui-Anatomie eines Messagingerweiterungsverwaltungsmenüs zeigt." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Unpin**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.|
|2|**Entfernen**: Entfernt die Messaging-Erweiterung aus dem Kanal, Chat oder Besprechung.|

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="setup-and-general-usage"></a>Setup und allgemeine Verwendung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel für Einrichtung und allgemeine Verwendung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Do: Integration mit Single-Sign on

SSO erleichtert, schneller und sicherer den Anmeldevorgang. Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich nicht erneut anmelden, um auf die Messagingerweiterung zuzugreifen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für die Integration mit Single-Sign On." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Nicht: Benutzer aus der Unterhaltung mitnehmen

Messagingerweiterungen sind Verknüpfungen, die die Kontextumschaltung reduzieren sollen. Ihre Erweiterung sollte benutzernicht z. B. zu einer Webseite außerhalb Teams.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Tun: Markieren Sie Ihre Messaging-Erweiterung

Messagingerweiterungen sind nicht immer leicht zu finden. Fügen Sie Screenshots zur Verwendung in Ihrer App-Detailseite ein. Wenn Ihre App auch einen Bot enthält, können Sie die Hilfedokumentation für messaging-Erweiterungen in eine Bot-Willkommenstour einschließen.

### <a name="templating"></a>Templating

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für die Vorlagenerstellung." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Tun: Lassen Sie Teams einige der Entwurfsarbeiten nach Möglichkeit erledigen

Wenn dies für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messagingerweiterung erstellen. Teams rendert diese Arten von Erweiterungen mit integrierter Thesierung und Zugänglichkeit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für die Handhabung von Konstruktionsarbeiten." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Nicht: Einbetten Der gesamten App in ein Aufgabenmodul

Wenn Ihre Messagingerweiterung Aktionsbefehle erfordert, halten Sie das Taskmodul einfach und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für die Themen." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Tun: Nutzen Sie Teams Farbtoken

Jedes Teams-Thema hat sein eigenes Farbschema. Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für Farbtoken." border="false":::

#### <a name="dont-hard-code-color-values"></a>Nicht: Harte Code-Farbwerte

Wenn Sie keine Teams Farbtoken verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Anspruch.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für Aktionen." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Tun: Einschließen von Aktionsbefehlen, die im Kontext sinnvoll sind

Nachrichtenaktionen sollten sich auf das beziehen, was ein Benutzer betrachtet. Stellen Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder einer Arbeitsaufgabe mithilfe des Texts im Beitrag einer Person bereit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für Aktionsbefehle." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a>Nicht: Einschließen von Aktionsbefehlen, die nicht kontextbezogen sind

Eine Nachrichtenaktion zum **Anzeigen Ihres Dashboards** scheint wahrscheinlich von den meisten Unterhaltungen getrennt zu sein.

   :::column-end:::
:::row-end:::

### <a name="searches"></a>Sucht

#### <a name="do-show-search-results-while-typing"></a>Tun: Anzeigen von Suchergebnissen während der Eingabe

Geben Sie vorgeschlagene Suchergebnisse an, während Benutzer eingeben. Sie können den Inhalt, den sie benötigen, schneller mit minimaler Anzahl von Zeichen finden.

#### <a name="dont-require-users-to-submit-a-query"></a>Nicht: Benutzer müssen eine Abfrage senden

Sie können Benutzer dazu veranlassen, eine Taste zu drücken oder eine Schaltfläche auszuwählen, um Abfragen an Ihre App zu senden. Auch wenn dies bei Ihrem App-Dienst einfacher sein kann, können die Personen verwirrt sein, dass sie beim Eingeben keine Echtzeit-Suchergebnisse sehen.

#### <a name="do-consider-zero-term-queries"></a>Tun: Betrachten Sie Null-Term-Abfragen

Wenn ein Benutzer beispielsweise etwas in das Suchfeld schreibt, zeigen Sie an, was er zuletzt in Ihrer App angezeigt hat. Es ist möglich, dass sie diesen Inhalt in ihre Unterhaltung einfügen möchten.
