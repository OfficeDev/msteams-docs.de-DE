---
title: Designregisterkarten für Desktop, Web und Mobile
description: Erfahren Sie, wie Sie eine Teams Registerkarte für Desktop, Web und Mobile entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a949687ee53186b4449ad086b4db6c89cc151995
ms.sourcegitcommit: 306b6e8cb3aac8bfda10ef3999467a797d64539d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2021
ms.locfileid: "58408629"
---
# <a name="design-your-tab-for-microsoft-teams"></a>Entwerfen Der Registerkarte für Microsoft Teams

Eine Registerkarte ist ein großer Zeichenbereich für Ihre App-Inhalte. Um Ihr App-Design zu leiten, beschreiben und veranschaulichen die folgenden Informationen, wie Benutzer Registerkarten in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Richtlinien für das Registerkartendesign, einschließlich Elementen, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit. Das UI-Kit enthält auch wichtige Themen wie Barrierefreiheit und dynamische Größenanpassung, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Registerkarte hinzufügen

Sie können eine Registerkarte aus dem Teams Store (AppSource) oder in einem der folgenden Kontexte hinzufügen:

* Chat
* Kanal
* Besprechung (vor, während oder nach der Besprechung)

### <a name="mobile"></a>Mobilgeräte

Benutzer können auf Registerkarten zugreifen, indem sie die Schaltfläche **"Mehr"** im Kanal (Beispiel unten) oder den Chat auswählen, in dem sie hinzugefügt wurden.

:::image type="content" source="../../assets/images/tabs/mobile-design-access-tab.png" alt-text="Beispiel zeigt, wie eine mobile Registerkarte in einem Kanal hinzugefügt wird." border="false":::

### <a name="desktop"></a>Desktop

Das folgende Beispiel zeigt, wie Benutzer eine Registerkarte in einem Kanal hinzufügen können.

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

## <a name="set-up-a-tab"></a>Einrichten einer Registerkarte

Es gibt einen kurzen Einrichtungsprozess, um eine App als Kanal, Chat oder Besprechungsregisterkarte hinzuzufügen. Die Erfahrung liegt größtenteils bei Ihnen. Sie könnten beispielsweise eine Beschreibung der Verwendung der App und einiger optionaler Einstellungen haben. Fügen Sie hier einen Anmeldeschritt ein, wenn Sie Benutzer authentifizieren müssen.

### <a name="tab-configuration-dialog"></a>Registerkartenkonfigurationsdialogfeld

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Beispiel zeigt eine modale Registerkartenkonfiguration." border="false":::

#### <a name="anatomy-tab-configuration-dialog"></a>Anatomie: Dialogfeld "Registerkartenkonfiguration"

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung der Ui-Anatomie einer modalen Registerkartenkonfiguration." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo:** Vollfarbiges App-Logo Ihrer App.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**iframe:** Dynamischer Speicherplatz für den Inhalt Ihrer App (z. B. Registerkarteneinstellungen oder Authentifizierung).|
|4 |**Infolink:** Öffnet ein Dialogfeld mit weiteren Informationen zur App, z. B. eine vollständige Beschreibung, von der App erforderliche Berechtigungen und Links zu Ihren Datenschutzrichtlinien und Nutzungsbedingungen.|
|5 |**Schaltfläche "Schließen":** Schließt das Dialogfeld.|
|6 |**Option "Teammitglieder benachrichtigen":** Im Dialogfeld werden Die Benutzer gefragt, ob sie einen Beitrag erstellen möchten, in dem andere darüber informiert werden, dass sie eine Registerkarte hinzugefügt haben.|
|7 |**Schaltfläche "Zurück":** Wechselt basierend auf dem geöffneten Dialogfeld zum vorherigen Schritt.|
|8 |**Schaltfläche "Speichern":** Schließt die Registerkarteneinrichtung ab.|

### <a name="tab-authentication-with-single-sign-on"></a>Registerkartenauthentifizierung mit einmaligem Anmelden

Sie können einen Schritt hinzufügen, in dem sich Benutzer zuerst mit ihren Microsoft-Anmeldeinformationen anmelden müssen. Diese Authentifizierungsmethode wird als Einmaliges Anmelden (Single Sign-On, SSO) bezeichnet.

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Beispiel zeigt einen Bildschirm für die Registerkartenauthentifizierung." border="false":::

### <a name="design-a-tab-setup-with-ui-templates"></a>Entwerfen eines Registerkartensetups mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams Ui-Vorlagen, um die Registerkarteneinrichtungsoberfläche zu entwerfen:

* [Liste:](../../concepts/design/design-teams-app-ui-templates.md#list)Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Zustand:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.

## <a name="view-a-tab"></a>Anzeigen einer Registerkarte

Registerkarten bieten eine Weboberfläche im Vollbildmodus in Teams, in der Sie Inhalte für die Zusammenarbeit wie Taskboards und Dashboards sowie wichtige Informationen anzeigen können.

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab.png" alt-text="Beispiel zeigt eine mobile Registerkarte mit einem Task Board." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Task Board." border="false":::

### <a name="anatomy-tab"></a>Anatomie: Registerkarte

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Registerkartenchat:** Öffnet einen Chat, mit dem Benutzer eine Unterhaltung neben dem Inhalt führen können.|
|3|**webview:** Zeigt Ihre App-Inhalte an.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung der Ui-Anatomie einer Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Registerkartenüberlauf:** Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.|
|3|**Registerkartenchat:** Öffnet einen Chat auf der rechten Seite, sodass Benutzer eine Unterhaltung neben dem Inhalt führen können.|
|4 |**iframe:** Zeigt Ihre App-Inhalte an.|

### <a name="design-a-tab-with-ui-templates-and-advanced-components"></a>Entwerfen einer Registerkarte mit Benutzeroberflächenvorlagen und erweiterten Komponenten

Verwenden Sie eine der folgenden Teams Vorlagen und Komponenten, um die Registerkartenerfahrung zu entwerfen:

* [Liste:](../../concepts/design/design-teams-app-ui-templates.md#list)Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Task Board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als "Tickets Board" oder "Sperre" bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen.
* [Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist eine Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Zustand:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.
* [Linke Navigation:](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Die linke Navigationskomponente kann hilfreich sein, wenn ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-a-tab-to-collaborate"></a>Verwenden einer Registerkarte für die Zusammenarbeit

Registerkarten erleichtern Unterhaltungen zu Inhalten an einem zentralen Ort.

### <a name="thread-discussion"></a>Diskussionsthread

Benutzer können automatisch Beiträge in einem Kanal oder Chat veröffentlichen, nachdem sie eine neue Registerkarte hinzugefügt haben. Dadurch werden Teammitglieder nicht nur über den neuen Inhalt benachrichtigt und ein Link zur Registerkarte bereitgestellt, sondern es können auch Personen beginnen, über die Registerkarte zu sprechen.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-channel.png" alt-text="Beispiel zeigt eine mobile Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanalthread behandelt wird." border="false":::

### <a name="tab-chat"></a>Registerkartenchat

Benutzer können eine Unterhaltung neben dem angezeigten Registerkarteninhalt führen. Auf dem Desktop wird der Chat an der Seite des App-Inhalts geöffnet.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine mobile Registerkarte mit einem Kontextchatbereich." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit geöffneten Chats auf der rechten Seite." border="false":::

### <a name="permissions-and-role-based-views"></a>Berechtigungen und rollenbasierte Ansichten

Die Registerkartenoberfläche kann für Benutzer je nach ihren Berechtigungen unterschiedlich sein. Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anmelden zu müssen. Ein anderer Benutzer muss sich jedoch anmelden und leicht unterschiedliche Inhalte sehen.

## <a name="manage-a-tab"></a>Verwalten einer Registerkarte

Sie können Optionen zum Umbenennen, Entfernen oder Ändern einer Registerkarte einschließen.

### <a name="anatomy-tab-menu"></a>Anatomie: Registerkartenmenü

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/tabs/mobile-design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines mobilen Registerkartenmenüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Im Browser öffnen:** Öffnet die App im Standardbrowser des Geräts.|
|2|**Link kopieren:** Benutzer können einen Link zu der Registerkarte kopieren und freigeben.|
|3|**Einstellungen:**(Optional) Ändern Sie die Einstellungen einer Registerkarte, nachdem sie hinzugefügt wurde.|
|4 |**Umbenennen:** Benutzer können der Registerkarte einen Namen geben, der für den Kanal, den Chat oder die Besprechung von Bedeutung ist.|
|5 |**Löschen:** Entfernt die Registerkarte aus dem Kanal, Chat oder der Besprechung.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Registerkartenmenüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Einstellungen**: (Optional) Ermöglicht Benutzern, die Einstellungen einer Registerkarte zu ändern, nachdem sie hinzugefügt wurde.|
|2|**Umbenennen:** Benutzer können der Registerkarte einen Namen geben, der für den Kanal, den Chat oder die Besprechung von Bedeutung ist.|
|3|**Entfernen:** Entfernt die Registerkarte aus dem Kanal, Chat oder der Besprechung.|

## <a name="tab-notifications-and-deep-linking"></a>Registerkartenbenachrichtigungen und Deep-Verknüpfung

Sie können eine Nachricht mit einem Deep-Link zu Ihrer Registerkarte senden. Eine Karte zeigt beispielsweise eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte anzuzeigen. Das Senden von Nachrichten über Registerkartenaktivitäten erhöht das Bewusstsein, ohne alle explizit zu benachrichtigen (d. h. Aktivität ohne Rauschen). Sie können bei Bedarf auch bestimmte Benutzer @mention.

Benachrichtigen Sie Benutzer über registerkartenaktivitäten auf eine der folgenden Arten:

* **Bot:** Diese Methode wird bevorzugt, insbesondere, wenn der Registerkartenthread zielgerichtet ist. Die Threadunterhaltung der Registerkarte wird als zuletzt aktiv in die Ansicht verschoben. Diese Methode ermöglicht auch eine gewisse Raffinesse bei der Art und Weise, wie die Benachrichtigung gesendet wird.
* **Nachricht:** Eine Nachricht wird im Aktivitätsfeed des Benutzers mit einem [Deep-Link zur Registerkarte angezeigt.](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine qualitativ hochwertige App-Erfahrung zu erstellen:

### <a name="collaboration"></a>Zusammenarbeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Die Abbildung zeigt, was mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a>Do: Unterhaltung vereinfachen

Einschließen von Inhalten und Komponenten, über die Personen sprechen können. Wenn es nicht in den Kontext eines Chats, Kanals oder einer Besprechung passt, gehört es nicht zu Ihrer Registerkarte.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Das Beispiel zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Don't: Treat your tab like any other webpage

Eine Registerkarte ist keine Webseite, die jemand einmal anzeigen kann. Auf einer Registerkarte sollten Ihre wichtigsten, relevanten Inhalte angezeigt werden, die Personen benötigen, um gemeinsam etwas zu erreichen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Beispiel, das zeigt, was mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Ausführen: Einschränken von Aufgaben und Daten

Registerkarten funktionieren am besten, wenn sie bestimmte Anforderungen erfüllen. Schließen Sie einen begrenzten Satz von Aufgaben und Daten ein, die für das Team oder die Gruppe relevant sind.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Nicht empfohlen: Einbetten der gesamten App

Die Verwendung einer Registerkarte zum Anzeigen einer gesamten App mit mehrstufiger Navigation und komplexen Interaktionen führt zu einer Informationsüberlastung.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Setup

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung, die zeigt, was mit dem Registerkarteneinrichtungsdesign zu tun ist." border="false":::

#### <a name="do-keep-it-simple"></a>Do: Halten Sie es einfach

Wenn Ihre App eine Authentifizierung erfordert, versuchen Sie, das einmalige Anmelden (Single Sign-On, SSO) von Microsoft zu integrieren, um eine nahtlosere Anmeldung zu ermöglichen. Fügen Sie außerdem nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte hinzu.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung, die zeigt, was nicht mit dem Registerkarteneinrichtungsdesign zu tun ist." border="false":::

#### <a name="dont-have-too-many-steps"></a>Don't: Have too many steps

Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Design

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Abbildung, die zeigt, was mit registerkartendesigns zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Was Sie tun sollten: Teams-Farbtoken nutzen

Jedes Teams-Design verfügt über ein eigenes Farbschema. Um Designänderungen automatisch zu verarbeiten, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Abbildung, die zeigt, was nicht mit Registerkartendesigns zu tun ist." border="false":::

#### <a name="dont-hard-code-color-values"></a>Was Sie nicht tun sollten: Hartcodieren von Farbwerten

Wenn Sie Teams Farbtoken nicht verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit für die Verwaltung.

   :::column-end:::
:::row-end:::
