---
title: Entwerfen der Registerkarte für Desktop und Webdienste
description: Hier erfahren Sie, wie Sie eine Registerkarte "Teams" (Desktop und Internet) entwerfen und das Microsoft Teams UI Kit abrufen.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 692a21c78dc86cbca5bf248e55d0332bd71c6b92
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604671"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a>Entwerfen der Registerkarte für Microsoft Teams Desktop und Internet

Eine Registerkarte ist eine große Leinwand für Inhalte, die die Zusammenarbeit erleichtert. Um Ihr App-Design zu führen, werden in den folgenden Informationen beschrieben und veranschaulicht, wie Benutzer Registerkarten in Microsoft Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Registerkarten-Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit. Das UI Kit enthält auch wichtige Themen wie Barrierefreiheit und Anpassungsfähigkeit, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Registerkarte hinzufügen

Sie können eine Registerkarte aus dem Microsoft Teams Store (AppSource) oder einen der folgenden Kontexte hinzufügen:

* Chat
* Kanal
* Besprechung (vor, während oder nach der Besprechung)

Im folgenden Beispiel wird gezeigt, wie eine Registerkarte in einem Kanal hinzugefügt wird.

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

## <a name="set-up-a-tab"></a>Einrichten einer Registerkarte

Es gibt einen kurzen Einrichtungsprozess, um eine App als Kanal, Chat oder Besprechungs Registerkarte hinzuzufügen. Die Erfahrung liegt weitgehend an Ihnen. Sie können beispielsweise eine Beschreibung der Verwendung der APP und einiger optionaler Einstellungen haben. Fügen Sie hier einen Anmelde Schritt ein, wenn Sie Benutzer authentifizieren müssen.

### <a name="tab-configuration-modal"></a>Modale Konfiguration der Registerkarte

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Beispiel zeigt eine modale Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-modal"></a>Anatomie: modale Konfiguration der Registerkarte

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung der Benutzeroberflächen Anatomie einer Registerkartenkonfiguration mit modaler Darstellung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo**: vollfarbiges App-Logo Ihrer APP.|
|2 |**App-Name**: vollständiger Name Ihrer APP.|
|3 |**iframe**: reaktionsfähiger Speicherplatz für den Inhalt Ihrer APP (beispielsweise Registerkarteneinstellungen oder Authentifizierung).|
|4 |**Info über Link**: öffnet ein Dialogfeld mit weiteren Informationen zur APP, beispielsweise eine vollständige Beschreibung, Berechtigungen, die für die APP erforderlich sind, sowie Links zu ihren Datenschutzrichtlinien und Nutzungsbedingungen.
|5 |**Schließen-Schaltfläche**: schließt den modal.|
|6 |**Teammitglieder Benachrichtigen Option**: das modale fragt, ob Sie einen Beitrag erstellen lassen möchten, bei dem andere wissen, dass Sie eine Registerkarte hinzugefügt haben.|
|7 |**Zurück-Schaltfläche**: wechselt zum vorherigen Schritt basierend auf der Stelle, an der das Dialogfeld geöffnet wurde.|
|8 |**Schaltfläche Speichern**: schließt das Registerkarten Setup ab.|

### <a name="tab-authentication-with-single-sign-on"></a>Tab-Authentifizierung mit einmaligem Anmelden

Sie können einen Schritt hinzufügen, in dem sich Benutzer zunächst mit Ihren Microsoft-Anmeldeinformationen anmelden müssen. Diese Authentifizierungsmethode wird als einmaliges Anmelden (Single Sign-on, SSO) bezeichnet.

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Beispiel zeigt einen Bildschirm für die Registerkarten Authentifizierung." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a>Entwerfen eines Registerkarten-Setups mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Microsoft Teams-Benutzeroberflächenvorlagen, die Ihnen bei der Gestaltung ihrer Registerkarten Einrichtung helfen:

* [List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.
* [Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.

## <a name="view-a-tab"></a>Anzeigen einer Registerkarte

Registerkarten bieten eine Vollbildfunktion in Microsoft Teams, in der Sie kollaborativen Inhalt anzeigen können – solche Aufgaben Bretter und Dashboards – und wichtige Informationen.

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Task Board." border="false":::

### <a name="anatomy-tab"></a>Anatomie: Registerkarte

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung der Benutzeroberflächen Anatomie einer Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Tab Name**: Navigations Bezeichnung für die Registerkarte.|
|2 |**Registerkarten Überlauf**: Öffnet Registerkarten Aktionen wie umbenennen und entfernen.|
|3 |**Tab Chat**: öffnet einen Chat-Thread auf der rechten Seite, sodass Benutzer eine Unterhaltung neben dem Inhalt haben.|
|4 |**iframe**: zeigt den Inhalt Ihrer Registerkarte an.

### <a name="designing-a-tab-with-ui-templates"></a>Entwerfen einer Registerkarte mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams-Benutzeroberflächenvorlagen, um die Gestaltung ihrer Tab-Oberfläche zu unterstützen:

* [List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.
* [Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): ein Aufgaben Gremium, das manchmal als Kanban-Board oder als Swim Lanes bezeichnet wird, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitsaufgaben oder Tickets verwendet werden.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): ein Dashboard ist eine Leinwand mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.
* [Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.
* [Linker NAV](../../concepts/design/design-teams-app-ui-templates.md#left-nav): die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-a-tab-to-collaborate"></a>Verwenden einer Registerkarte für die Zusammenarbeit

Mithilfe von Registerkarten können Unterhaltungen zu Inhalten an einem zentralen Ort erleichtert werden.

### <a name="thread-discussion"></a>Thread Diskussion

Benutzer können automatisch in einem Kanal oder Chat Posten, nachdem Sie eine neue Registerkarte hinzugefügt haben. Dies benachrichtigt nicht nur Teammitglieder über den neuen Inhalt und stellt einen Link zur Registerkarte zur Verfügung, damit die Benutzer über die Registerkarte sprechen können.

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Beispiel zeigt eine Registerkarte, die in einem Kanal Thread erörtert wird." border="false":::

### <a name="side-by-side-discussion"></a>Parallele Diskussionen

Benutzer können beim Anzeigen des Inhalts der Registerkarte eine Unterhaltung als nächstes haben.

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit geöffnetem Chat auf der rechten Seite." border="false":::

### <a name="permissions-and-role-based-views"></a>Berechtigungen und rollenbasierte Ansichten

Die Registerkarte kann für Benutzer je nach Ihren Berechtigungen unterschiedlich sein. Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anzumelden. Ein anderer Benutzer muss jedoch leicht unterschiedliche Inhalte unterzeichnen und sehen.

## <a name="manage-a-tab"></a>Verwalten einer Registerkarte

Sie können Optionen einschließen, um eine Registerkarte umzubenennen, zu entfernen oder zu ändern.

### <a name="anatomy-tab-menu"></a>Anatomie: Register Menü

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung der Benutzeroberflächen Anatomie eines Registerkarten Menüs" border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Settings**: (optional) ermöglicht Benutzern, die Einstellungen einer Registerkarte zu ändern, nachdem Sie hinzugefügt wurde.|
|2 |**Umbenennen**: ermöglicht Benutzern, der Registerkarte einen Namen zu geben, der für das Team aussagekräftiger ist.|
|3 |**Remove**: entfernt die Registerkarte aus dem Kanal, dem Chat oder der Besprechung.|

## <a name="tab-notifications-and-deep-linking"></a>Registerkarten Benachrichtigungen und Deep Linking

Sie können eine Nachricht mit einem Deep-Link an Ihre Registerkarte senden. Beispielsweise zeigt eine Karte eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte anzuzeigen. Durch das Senden von Nachrichten zur Tab-Aktivität wird die Bekanntheit erhöht, ohne dass alle Personen explizit benachrichtigt werden (also Aktivität ohne Rauschen). Bei Bedarf können Sie auch bestimmte Benutzer @mention.

Benutzer von Tab-Aktivität auf eine der folgenden Arten Benachrichtigen:

* **Bot**: Diese Methode wird vor allem bevorzugt, wenn der Tab-Thread gezielt ist. Die threaded-Unterhaltung der Registerkarte wird als kürzlich aktiviert in die Ansicht verschoben. Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.
* **Meldung**: eine Nachricht wird im Aktivitätsfeed des Benutzers mit einem [tiefen Link zur Registerkarte](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)angezeigt.

## <a name="best-practices"></a>Bewährte Methoden

### <a name="collaboration"></a>Zusammenarbeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a>Do: Unterstützung für Unterhaltungen

Inhalte und Komponenten einbeziehen, über die Menschen sprechen können. Wenn er nicht in den Kontext eines Chats, Kanals oder einer Besprechung passt, gehört er nicht in Ihre Registerkarte.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Illustration, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Nicht: behandeln ihrer Registerkarte wie jede andere Webseite

Eine Registerkarte ist keine Webseite, die von jemand einmal angezeigt werden kann. Auf einer Registerkarte sollten Ihre wichtigsten, relevanten Inhalte angezeigt werden, die die Benutzer benötigen, um gemeinsam etwas zu erreichen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Do: begrenzen von Vorgängen und Daten

Registerkarten funktionieren am besten, wenn Sie bestimmte Anforderungen erfüllen. Einschließen einer begrenzten Gruppe von Aufgaben und Daten, die für das Team oder die Gruppe relevant sind.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Illustration, die zeigt, was nicht mit dem Design der Registerkartennavigation zu tun ist." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Nicht: Einbetten der gesamten App

Die Verwendung einer Registerkarte zum Anzeigen einer ganzen app mit mehrstufiger Navigation und komplexen Interaktionen führt zu Informationsüberlastung.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Setup

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung, die zeigt, was mit dem Design der Registerkarten Einrichtung geschieht." border="false":::

#### <a name="do-keep-it-simple"></a>Do: einfache Aufbewahrung

Wenn Ihre APP eine Authentifizierung erfordert, versuchen Sie, Microsoft Single Sign-on (SSO) zu integrieren, um eine nahtlose Anmeldung zu erzielen. Schließen Sie außerdem nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte ein.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung zeigt, was mit dem Design der Registerkarten Einrichtung nicht getan werden kann." border="false":::

#### <a name="dont-have-too-many-steps"></a>Nicht: zu viele Schritte

Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Illustration, die zeigt, was mit der Tab-Funktion zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Do: nutzen Sie die Vorteile von Microsoft Teams-Farb Token

Jedes Microsoft Teams-Design verfügt über ein eigenes Farbschema. Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farb Token (Fluent UI)</a> in Ihrem Design.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Illustration, die zeigt, was mit der Tab-Funktion nicht getan werden kann." border="false":::

#### <a name="dont-hard-code-color-values"></a>Nicht: Farb Werte mit festem Code

Wenn Sie keine Microsoft Teams-Farb Token verwenden, sind Ihre Designs weniger skalierbar und benötigen mehr Zeit zum Verwalten.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
