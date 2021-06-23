---
title: Entwerfen Sie Ihre Messaging-Erweiterung
description: Erfahren Sie, wie Sie eine Teams-Messaging-Erweiterung entwerfen und das Microsoft Teams-UI-Kit erhalten.
keywords: Richtlinien für Teams-Entwurfsreferenzen für Messaging-Erweiterungs-Tips – Bewährte Methode
author: heath-hamilton
localization_priority: Priority
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: f4d1ba1e6e0b71b37e2b7b2d2a32fb729822ba1c
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037670"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a>Entwerfen Sie Ihre Microsoft Teams-Messaging-Erweiterung

Messagingerweiterungen sind Tastenkombinationen zum Einfügen von App-Inhalten oder zum Bearbeiten einer Nachricht, ohne von der Konversation weg zu navigieren.
Um Ihr App-Design zu steuern, beschreiben und veranschaulichen die folgenden Informationen, wie Benutzer Messagingerweiterungen in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Richtlinien für den Entwurf von Messaging-Erweiterungen, einschließlich Elementen, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a>Hinzufügen einer Messaging-Erweiterung

In den folgenden Teams-Kontexten können eine Messaging-Erweiterung hinzufügen:

* Aus dem Teams-Store.
* In einem Kanal, Chat oder einer Besprechung (vor, während und nachher) in der Nähe des "Verfassen"-Felds. Beachten Sie, dass wenn Sie eine Messaging-Erweiterung an einer dieser Stellen hinzufügen, nur Sie sie in diesem Kontext verwenden können.

Das folgende Beispiel zeigt, wie Sie eine Messaging-Erweiterung in einem Kanal hinzufügen:

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Das Beispiel zeigt, wie eine Messaging-Erweiterung in der Nähe des &quot;Verfassen&quot;-Felds in einem Kanal hinzugefügt wird." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-add-in-channel.png" alt-text="Das Beispiel zeigt, wie eine Messaging-Erweiterung in der Nähe des &quot;Verfassen&quot;-Felds in einem Kanal auf Mobilgeräten hinzugefügt wird." border="false":::

---

## <a name="set-up-a-messaging-extension"></a>Einrichten einer Messaging-Erweiterung

Die Authentifizierung ist nicht obligatorisch, aber wenn Ihre App zum Beispiel eine Art Ticketverfolgungstool ist, müssen Sie sich Benutzer möglicherweise anmelden, um die Messaging-Erweiterung zu verwenden.

Aus Gründen der Konsistenz zwischen Teams-Apps können Sie den Anmeldebildschirm nicht anpassen. Wenn Sie die Authentifizierung mit einmaligem Anmelden (Single Sign-On, SSO) verwenden, werden Benutzer automatisch angemeldet.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Das Beispiel zeigt den Setupbildschirm der Messaging-Erweiterung mit einer Anmeldeschaltfläche." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-set-up.png" alt-text="Das Beispiel zeigt den Setupbildschirm der Messaging-Erweiterung mit einer Anmeldeschaltfläche auf Mobilgeräten." border="false":::

---

## <a name="types-of-messaging-extensions"></a>Typen von Messaging-Erweiterungen

Messaging-Erweiterungen können Suchbefehle, Aktionsbefehle oder beides aufweisen. Ihre Befehle hängen von den Features Ihrer App und davon ab, wie diese in Teams-Anwendungsfälle passen.

### <a name="search-commands"></a>Suchbefehle

Mit Suchbefehlen können Benutzer Ihre Messaging-Erweiterung dazu nutzen, schnell externe Inhalte zu finden und in eine Nachricht einzufügen. Suchbefehle werden häufig im "Verfassen"-Feld zur Verfügung gestellt. Sie können z. B. eine Diskussion beginnen oder etwas zu einer Diskussion hinzufügen, indem Sie einen Teil des Inhalts teilen – ohne Teams verlassen zu müssen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Messaging-Erweiterung, die über das &quot;Verfassen&quot;-Feld gestartet wurde." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-search-command-type.png" alt-text="Das Beispiel zeigt eine suchbasierte Messaging-Erweiterung, die über das &quot;Verfassen&quot;-Feld auf mobilen Geräten gestartet wurde." border="false":::

---

#### <a name="compose-box-layout-options"></a>Layoutoptionen für das "Verfassen"-Feld 

Sie haben einige Optionen zum Anzeigen von Suchergebnissen für Messaging-Erweiterung, einschließlich [Listen- und Rasteransichten](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Abbildungen mit Layoutoptionen für Suchergebnisse von Messaging-Erweiterung." border="false":::

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle ermöglichen es Personen, Aktionen auszulösen und Anforderungen in externen Diensten in Teams zu verarbeiten. Wenn Ihre App beispielsweise Bestellungen nachverfolgt, kann ein Benutzer eine neue Bestellung erstellen, indem er den Inhalt der Nachricht eines Kollegen direkt in seinem Chat verwendet.

Aktionsbasierte Messaging-Erweiterungen erfordern häufig, dass Benutzer ein Formular oder eine andere Art von Konfiguration innerhalb eines Modals ausfüllen müssen. Sie können diese Erfahrungen mit [Aufgabenmodulen](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)erstellen.

## <a name="open-a-messaging-extension"></a>Öffnen einer Messaging-Erweiterung

Das "Verfassen"-Feld und Nachrichten oder Beiträge sind die primären Kontexte, in denen Benutzer Messaging-Erweiterungen verwenden.

### <a name="from-the-compose-box"></a>Über das "Verfassen"-Feld

Nach dem Hinzufügen können Benutzer Ihre Messaging-Erweiterung öffnen, indem sie ihr App-Symbol unter dem "Verfassen"-Feld auswählen. In diesen Beispielen verfügt die Erweiterung über Such- und Aktionsbefehle.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung über das &quot;Verfassen&quot;-Feld öffnen." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-compose-box.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung über das &quot;Verfassen&quot;-Feld auf Mobilgeräten öffnen." border="false":::

---

### <a name="from-a-chat-message-or-channel-post"></a>Aus einer Chatnachricht oder einem Kanalbeitrag

Nach dem Hinzufügen können Benutzer das Symbol **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: in der Chatnachricht oder im Kanalbeitrag auswählen, um die Aktionsbefehle Ihrer Erweiterung zu finden. Ihre Erweiterung wird möglicherweise basierend auf der Nutzung unter **Weitere Aktionen** aufgeführt.

> [!NOTE]
> Unterstützung für weitere Aktionen aus einer Chatnachricht oder einem Kanalbeitrag ist auf der mobilen Microsoft Teams-Plattform nicht verfügbar. 

#### <a name="chat-message"></a>Chatnachricht

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung aus einer Chatnachricht öffnen." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-chat-post.png" alt-text="Das Beispiel zeigt, wie Sie eine Messaging-Erweiterung aus einem Chatbeitrag auf mobilen Geräten öffnen." border="false":::

---
':::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
':::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
---

## <a name="use-a-messaging-extension"></a>Verwenden einer Messaging-Erweiterung

In den folgenden Szenarien wird veranschaulicht, wie Benutzer Messaging-Erweiterungen in erster Linie verwenden.

### <a name="insert-content-into-a-message"></a>Einfügen von Inhalt in eine Nachricht

**1. Wählen Sie eine Messaging-Erweiterung aus**. Benutzer können über das "Verfassen"-Feld nach dem Inhalt suchen, den sie freigeben möchten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der nach Inhalten sucht, die aus dem &quot;Verfassen&quot;-Feld eingefügt werden sollen." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-search.png" alt-text="Das Beispiel zeigt einen Benutzer, der auf einem Mobilgerät über das &quot;Verfassen&quot;-Feld nach Inhalten sucht, die eingefügt werden sollen." border="false":::

---

**2. Inhalt einfügen**. Nach der Veröffentlichung können andere Personen auf den Inhalt antworten oder diesen auswählen, um weitere Informationen in Ihrer App anzuzeigen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Das Beispiel zeigt, wie ein Benutzer Inhalte in einer Kanalunterhaltung postet." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-posted.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät Inhalte in einer Kanalunterhaltung postet." border="false":::

---

### <a name="take-action-on-a-message"></a>Aktionen für eine Nachricht ausführen

**1. Wählen Sie eine Messaging-Erweiterung aus**. Ihre App kann einen oder mehrere Aktionsbefehle enthalten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Aktionsbefehl für die Messaging-Erweiterung auswählt." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-select-action-command.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät einen Aktionsbefehl für die Messaging-Erweiterung auswählt." border="false":::

---

**2. Führen Sie die Aktion aus**. Ihre App kann alle Inhalte oder Daten empfangen und verarbeiten, die von der Nachrichtenaktion gesendet werden. Dadurch können Benutzer in ihrer Unterhaltung bleiben und sich keine Gedanken über die direkte Eingabe von Informationen in Ihrer App machen, wie im folgenden Beispiel.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Beispiel für das Ausführen von Aktionen für eine Nachricht." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-complete-action-command.png" alt-text="Beispiel für das Ausführen von Aktionen für eine Nachricht auf einem Mobilgerät." border="false":::

---

### <a name="preview-links"></a>Vorschaulinks

Messaging-Erweiterungen ermöglichen es Ihnen auch, Rich-Links aus einer erkannten URL in eine Nachricht einzufügen. (Diese Funktion wird als[Entfalten von Links](../../messaging-extensions/how-to/link-unfurling.md)bezeichnet).

**1. Fügen Sie einen erkannten Link** in das "Verfassen"-Feld ein.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer einen Link in das &quot;Verfassen&quot;-Feld eingibt." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-paste-preview-link.png" alt-text="Das Beispiel zeigt, wie ein Benutzer auf einem Mobilgerät einen Link in das &quot;Verfassen&quot;-Feld eingibt." border="false":::

---

**2. Inhalt einfügen**. Wenn Ihre App die URL im "Verfassen"-Feld erkennt, rendert sie den Link als Karte, die eine inhaltsreiche Vorschau des Webinhalts bereitstellt. (Weitere Informationen finden Sie unter [Entwurfsrichtlinien für Adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md).)

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL umfangreiche Inhalte in das &quot;Verfassen&quot;-Feld einschließt, da sie von Ihrer App erkannt wird." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-preview-link.png" alt-text="Das Beispiel zeigt, wie die URL auf einem Mobilgerät umfangreiche Inhalte in das &quot;Verfassen&quot;-Feld einschließt, da sie von Ihrer App erkannt wird." border="false":::

---

## <a name="manage-a-messaging-extension"></a>Verwalten einer Messaging-Erweiterung

Benutzer können Ihre Messaging-Erweiterung anheften, entfernen oder konfigurieren, wenn Sie mit der rechten Maustaste auf Ihr Symbol klicken.

## <a name="anatomy"></a>Anatomie

### <a name="messaging-extension-in-the-compose-box"></a>Messaging-Erweiterung im "Verfassen"-Feld

Das folgende Beispiel ist eine Messaging-Erweiterung, die über das "Verfassen"-Feld geöffnet wird.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Abbildung zeigt die UI-Anatomie einer Messaging-Erweiterung im Feld &quot;Verfassen&quot;." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo**: Farbsymbol Ihres App-Logos.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Menüsymbol für Aktionsbefehle (optional)**: Öffnet eine Liste von Aktionsbefehlen für Ihre Messaging-Erweiterung (sofern vorhanden).
|4|**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.|
|5|**Registerkartenmenü (optional)**: Stellt mehrere Inhaltskategorien bereit.|
|6|**Menü "Aktionsbefehle" (optional)**: Zeigt die Liste der Aktionsbefehle an (sofern angegeben).|
|7|**App-Inhalt**: Hauptsächlich zum Anzeigen von Suchergebnissen. Im folgenden Beispiel wird das Listenlayout verwendet (Rasterlayout ist eine weitere Option).|
|8|**App-Logo**: Gliederungssymbol Ihres App-Logos.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-anatomy-compose.png" alt-text="Abbildung zeigt die UI-Anatomie einer Messaging-Erweiterung im Feld &quot;Verfassen&quot;auf einem Mobilgerät." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Name**: Vollständiger Name Ihrer App.|
|2|**Menüsymbol für Aktionsbefehle (optional)**: Öffnet eine Liste von Aktionsbefehlen für Ihre Messaging-Erweiterung (sofern vorhanden).
|3|**Suchfeld**: Ermöglicht Benutzern das Suchen von App-Inhalten, die sie einfügen möchten.|
|4|**Registerkartenmenü (optional)**: Stellt mehrere Inhaltskategorien bereit.|
|5|**Menü "Aktionsbefehle" (optional)**: Zeigt die Liste der Aktionsbefehle an (sofern angegeben).|
|6|**App-Inhalt**: Hauptsächlich zum Anzeigen von Suchergebnissen.|

---

### <a name="messaging-extension-management-menu"></a>Menü "Verwalten der Messaging-Erweiterung"

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Abbildung zeigt die UI-Anatomie eines &quot;Verwalten der Messaging-Erweiterung&quot;-Menüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Lösen sie**: Verfügbar, wenn der Benutzer Ihre App angeheftet hat.|
|2|**Entfernen**: Entfernt die Messaging-Erweiterung aus dem Kanal, Chat oder der Besprechung.|

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="setup-and-general-usage"></a>Setup und allgemeine Nutzung

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Beispiel für Setup und allgemeine Nutzung." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a>Was Sie tun sollten: Integration mit einmaligem Anmelden

Einmaliges Anmelden vereinfacht, beschleunigt und schützt den Anmeldevorgang. Wenn sich ein Benutzer bereits bei Ihrer persönlichen App angemeldet hat, muss er sich auch nicht erneut anmelden, um auf die Messaging-Erweiterung zuzugreifen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Beispiel für die Integration mit einmaligem Anmelden." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a>Was Sie nicht tun sollten: Benutzer aus der Unterhaltung entfernen

Messaging-Erweiterungen sind Tastenkombinationen, die den Kontextwechsel reduzieren sollen. Ihre Erweiterung sollte Benutzer beispielsweise nicht zu einer Webseite außerhalb von Teams weiterleiten.

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a>Was Sie tun sollten: Hervorheben Ihrer Messaging-Erweiterung

Messaging-Erweiterungen sind nicht immer leicht zu finden. Fügen Sie Screenshots zur Verwendungsweise auf der Detailseite Ihrer App ein. Wenn Ihre App auch einen Bot enthält, können Sie die Hilfedokumentation zur Messaging-Erweiterung in eine Bot-Willkommenstour aufnehmen.

### <a name="templating"></a>Vorlagen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Beispiel für Vorlagen." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a>Was Sie tun sollten: Lassen Sie Teams nach Möglichkeit einen Teil der Entwurfsarbeit erledigen

Wenn es für Ihre Anwendungsfälle sinnvoll ist, sollten Sie eine suchbasierte Messaging-Erweiterung erstellen. Teams rendert diese Arten von Erweiterungen mit integriertem Design und Barrierefreiheit.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Beispiel für die Verarbeitung von Entwurfsarbeiten." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a>Was Sie nicht tun sollten: Einbetten der gesamten App in ein Aufgabenmodul

Wenn Ihre Messaging-Erweiterung Aktionsbefehle erfordert, halten Sie das Aufgabenmodul schlicht, und zeigen Sie nur die Komponenten an, die zum Abschließen der Aktion erforderlich sind.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Design

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Beispiel für Design." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Was Sie tun sollten: Teams-Farbtoken nutzen

Jedes Teams-Design verfügt über ein eigenes Farbschema. Um Designänderungen automatisch zu verarbeiten, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Beispiel für Farbtoken." border="false":::

#### <a name="dont-hard-code-color-values"></a>Was Sie nicht tun sollten: Hartcodieren von Farbwerten

Wenn Sie keine Teams-Farbtoken verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit für die Verwaltung.

   :::column-end:::
:::row-end:::

### <a name="actions"></a>Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Beispiel für Aktionen." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a>Was Sie tun sollten: Aktionsbefehle einschließen, die im Kontext sinnvoll sind

Nachrichtenaktionen sollten sich auf das beziehen, was ein Benutzer sieht. Geben Sie Benutzern beispielsweise eine Verknüpfung zum Erstellen eines Problems oder Arbeitselements mithilfe des Texts in einem Beitrag einer Person an.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Beispiel für Aktionsbefehle." border="false":::

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
