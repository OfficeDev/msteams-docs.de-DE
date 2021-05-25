---
title: Entwerfen Ihrer Registerkarte für Desktop und Web
description: Erfahren Sie, wie Sie Teams Registerkarte (Desktop und Web) entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 38eb7e400de63beb0d2840ee573bbfd16299cfbd
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644713"
---
# <a name="designing-your-tab-for-microsoft-teams"></a>Entwerfen Ihrer Registerkarte für Microsoft Teams

Eine Registerkarte ist ein großer Canvas für Ihre App-Inhalte. Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Registerkarten hinzufügen, verwenden und verwalten Teams.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Richtlinien für das Registerkartendesign, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit. Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Registerkarte hinzufügen

Sie können eine Registerkarte aus dem Teams (AppSource) oder in einem der folgenden Kontexte hinzufügen:

* Chat
* Kanal
* Besprechung (vor, während oder nach der Besprechung)

# <a name="desktop"></a>[Desktop](#tab/desktop)

Das folgende Beispiel zeigt, wie Benutzer eine Registerkarte in einem Kanal hinzufügen können.

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Benutzer können auf Registerkarten zugreifen, indem sie die Schaltfläche **Mehr** im Kanal (Beispiel unten) oder chatten, in dem sie hinzugefügt wurden.

:::image type="content" source="../../assets/images/tabs/mobile-design-access-tab.png" alt-text="Beispiel zeigt eine mobile Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

---

## <a name="set-up-a-tab"></a>Einrichten einer Registerkarte

Es gibt einen kurzen Einrichtungsprozess zum Hinzufügen einer App als Kanal, Chat oder Besprechungsregisterkarte. Die Erfahrung liegt weitgehend bei Ihnen. Sie könnten beispielsweise eine Beschreibung der Verwendung der App und einige optionale Einstellungen haben. Schließen Sie hier einen Anmeldeschritt ein, wenn Sie Benutzer authentifizieren müssen.

### <a name="tab-configuration-dialog"></a>Dialogfeld "Registerkartenkonfiguration"

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Beispiel zeigt eine modale Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-dialog"></a>Anatomie: Dialogfeld "Registerkartenkonfiguration"

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung der Ui-Anatomie einer modalen Registerkartenkonfiguration." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo:** Vollfarbiges App-Logo Ihrer App.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**iframe**: Responsive space for your app's content (for example, tab settings or authentication).|
|4 |**Über Link**: Öffnet ein Dialogfeld, in dem weitere Informationen zur App angezeigt werden, z. B. eine vollständige Beschreibung, von der App erforderliche Berechtigungen und Links zu Ihrer Datenschutzrichtlinie und den Nutzungsbedingungen.|
|5 |**Schaltfläche Schließen**: Schließt das Dialogfeld.|
|6 |**Option Teammitglieder benachrichtigen:** Im Dialogfeld werden Benutzer gefragt, ob sie einen Beitrag erstellen möchten, der andere darüber informiert, dass sie eine Registerkarte hinzugefügt haben.|
|7 |**Schaltfläche "Zurück":** Geht zum vorherigen Schritt, basierend auf dem Ort, an dem das Dialogfeld geöffnet wurde.|
|8 |**Schaltfläche "Speichern":** Schließt die Registerkarteneinrichtung ab.|

### <a name="tab-authentication-with-single-sign-on"></a>Registerkartenauthentifizierung mit einmaligem Anmelden

Sie können einen Schritt hinzufügen, in dem sich Benutzer zuerst mit ihren Microsoft-Anmeldeinformationen anmelden müssen. Diese Authentifizierungsmethode wird als einmaliges Anmelden (Single Sign-On, SSO) bezeichnet.

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Beispiel zeigt einen Registerkartenauthentifizierungsbildschirm." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a>Entwerfen einer Registerkarteneinrichtung mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams- und Benutzeroberflächenvorlagen, um beim Entwerfen der Registerkarteneinrichtung zu helfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.
* [Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.

## <a name="view-a-tab"></a>Anzeigen einer Registerkarte

Registerkarten bieten eine Vollbildweberfahrung in Teams, in der Sie gemeinsamen Inhalt ( z. B. Aufgabenboards und Dashboards ) und wichtige Informationen anzeigen können.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Aufgabenboard." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab.png" alt-text="Beispiel zeigt eine mobile Registerkarte mit einem Aufgabenboard." border="false":::

---

### <a name="anatomy-tab"></a>Anatomie: Registerkarte

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.|
|3|**Tab-Chat:** Öffnet einen Chat auf der rechten Seite, sodass Benutzer neben dem Inhalt eine Unterhaltung führen können.|
|4 |**iframe**: Zeigt Ihre App-Inhalte an.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Tab-Chat:** Öffnet einen Chat, mit dem Benutzer neben dem Inhalt eine Unterhaltung führen können.|
|3|**webview**: Zeigt Ihre App-Inhalte an.|

---

### <a name="designing-a-tab-with-ui-templates-and-advanced-components"></a>Entwerfen einer Registerkarte mit Benutzeroberflächenvorlagen und erweiterten Komponenten

Verwenden Sie eine der folgenden Teams Und-Komponenten, um Ihre Registerkartenerfahrung zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.
* [Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.
* [Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.
* [Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.
* [Linkes](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Navigationselement: Die linke Navigationskomponente kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-a-tab-to-collaborate"></a>Verwenden einer Registerkarte für die Zusammenarbeit

Registerkarten erleichtern Unterhaltungen über Inhalte an einem zentralen Ort.

### <a name="thread-discussion"></a>Threaddiskussion

Benutzer können automatisch in einem Kanal oder Chat posten, nachdem sie eine neue Registerkarte hinzugefügt haben. Dies benachrichtigt nicht nur Teammitglieder über den neuen Inhalt und stellt einen Link zur Registerkarte zur Seite, sondern ermöglicht es Benutzern, über die Registerkarte zu sprechen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-channel.png" alt-text="Beispiel zeigt eine mobile Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

---

### <a name="tab-chat"></a>Registerkartenchat

Benutzer können neben den angezeigten Registerkarteninhalten eine Unterhaltung führen. Auf dem Desktop wird der Chat an der Seite des App-Inhalts geöffnet.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit einem auf der rechten Seite geöffneten Chat." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine mobile Registerkarte mit einem kontextbezogenen Chatbereich." border="false":::

---

### <a name="permissions-and-role-based-views"></a>Berechtigungen und rollenbasierte Ansichten

Die Registerkartenerfahrung kann für Benutzer je nach ihren Berechtigungen unterschiedlich sein. Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anmelden zu müssen. Ein anderer Benutzer muss sich jedoch signieren und sieht leicht andere Inhalte.

## <a name="manage-a-tab"></a>Verwalten einer Registerkarte

Sie können Optionen zum Umbenennen, Entfernen oder Ändern einer Registerkarte hinzufügen.

### <a name="anatomy-tab-menu"></a>Anatomie: Registerkartenmenü

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Registerkartenmenüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Einstellungen**: (Optional) Ermöglicht Benutzern das Ändern der Einstellungen einer Registerkarte, nachdem sie hinzugefügt wurde.|
|2|**Umbenennen:** Benutzer können der Registerkarte einen Namen geben, der für den Kanal, den Chat oder die Besprechung von Bedeutung ist.|
|3|**Remove**: Entfernt die Registerkarte aus dem Kanal, Chat oder besprechung.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines mobilen Registerkartenmenüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Öffnen im Browser**: Öffnet die App im Standardbrowser des Geräts.|
|2|**Link kopieren:** Benutzer können einen Link zur Registerkarte kopieren und freigeben.|
|3|**Einstellungen**: (Optional) Ändern Sie die Einstellungen einer Registerkarte, nachdem sie hinzugefügt wurde.|
|4 |**Umbenennen:** Benutzer können der Registerkarte einen Namen geben, der für den Kanal, den Chat oder die Besprechung von Bedeutung ist.|
|5 |**Löschen**: Entfernt die Registerkarte aus dem Kanal, Chat oder der Besprechung.|

---

## <a name="tab-notifications-and-deep-linking"></a>Registerkartenbenachrichtigungen und tiefe Verknüpfungen

Sie können eine Nachricht mit einem tiefen Link zu Ihrer Registerkarte senden. Beispielsweise zeigt eine Karte eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte zu sehen. Das Senden von Nachrichten zu Registerkartenaktivitäten erhöht das Bewusstsein, ohne dass alle Benutzer (d. h. Aktivitäten ohne Geräusche) explizit benachrichtigt werden. Sie können auch @mention benutzer bei Bedarf.

Benachrichtigen Sie Die Benutzer über die Registerkartenaktivität auf eine der folgenden Weisen:

* **Bot**: Diese Methode wird vor allem dann bevorzugt, wenn der Registerkartenthread gezielt ist. Die Thread-Unterhaltung der Registerkarte wird als zuletzt aktiv angezeigt. Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.
* **Nachricht**: Eine Nachricht wird im Aktivitätsfeed des Benutzers mit einem tiefen [Link zur Registerkarte angezeigt.](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen:

### <a name="collaboration"></a>Zusammenarbeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Abbildung zeigt, was mit dem Registerkartennavigationsdesign zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a>Do: Unterhaltung erleichtern

Fügen Sie Inhalte und Komponenten ein, über die Personen sprechen können. Wenn sie nicht in den Kontext eines Chats, Kanals oder einer Besprechung passt, gehört sie nicht zu Ihrer Registerkarte.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Beispiel zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Don't: Behandeln Ihrer Registerkarte wie jede andere Webseite

Eine Registerkarte ist keine Webseite, die jemand einmal anzeigen kann. Auf einer Registerkarte sollten Ihre wichtigsten, relevanten Inhalte angezeigt werden, die die Personen benötigen, um gemeinsam etwas zu erreichen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Beispiel, in dem gezeigt wird, was mit dem Registerkartennavigationsdesign zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Do: Einschränken von Aufgaben und Daten

Registerkarten funktionieren am besten, wenn sie bestimmte Anforderungen erfüllen. Schließen Sie eine begrenzte Anzahl von Aufgaben und Daten ein, die für das Team oder die Gruppe relevant sind.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Don't: Embed your entire app

Die Verwendung einer Registerkarte zum Anzeigen einer gesamten App mit mehrstufiger Navigation und komplexen Interaktionen führt zu Einer Informationsüberlastung.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Setup

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkarteneinrichtung zu tun ist." border="false":::

#### <a name="do-keep-it-simple"></a>Do: Keep it simple

Wenn Ihre App eine Authentifizierung erfordert, versuchen Sie, Microsoft single sign-on (SSO) zu integrieren, um eine nahtlose Anmeldung zu ermöglichen. Fügen Sie außerdem nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte hinzu.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkarteneinrichtung zu tun ist." border="false":::

#### <a name="dont-have-too-many-steps"></a>Don't: Have too many steps

Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Abbildung, die zeigt, was mit dem Registerkarten-Theming zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Do: Nutzen Teams Farbtoken

Jedes Teams design verfügt über ein eigenes Farbschema. Verwenden Sie Farbtoken <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">(Fluent UI)</a> in Ihrem Entwurf, um Designänderungen automatisch zu verarbeiten.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Abbildung, die zeigt, was nicht mit Registerkarten-Theming zu tun ist." border="false":::

#### <a name="dont-hard-code-color-values"></a>Don't: Hartcodefarbwerte

Wenn Sie keine Teams verwenden, sind Ihre Designs weniger skalierbar und nehmen sich mehr Zeit für die Verwaltung.

   :::column-end:::
:::row-end:::
