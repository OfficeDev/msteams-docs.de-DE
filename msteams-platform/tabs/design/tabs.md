---
title: Entwerfen Ihrer Registerkarte für Desktop und Web
description: Erfahren Sie, wie Sie eine Teams Registerkarte (Desktop und Web) entwerfen und das Microsoft Teams UI Kit abrufen.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: baa17cd97ff4e2cad91615dced5c4e4cf5e533c8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566880"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a>Entwerfen der Registerkarte für Microsoft Teams Desktop und Web

Eine Registerkarte ist ein großer Canvas für Ihre Inhalte. Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer Registerkarten in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Richtlinien für den Tab-Design, einschließlich Elemente, die Sie bei Bedarf greifen und ändern können, finden Sie im Microsoft Teams UI Kit. Das UI-Kit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a>Registerkarte hinzufügen

Sie können eine Registerkarte aus dem Teams Store (AppSource) oder in einem der folgenden Kontexte hinzufügen:

* Chat
* Kanal
* Besprechung (vor, während oder nach der Besprechung)

Das folgende Beispiel zeigt, wie eine Registerkarte in einem Kanal hinzugefügt wird:

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Das Beispiel zeigt eine Registerkarte, die in einem Kanal hinzugefügt wird." border="false":::

## <a name="set-up-a-tab"></a>Einrichten einer Registerkarte

Es gibt einen kurzen Einrichtungsprozess, um eine App als Kanal, Chat oder Besprechungsregisterkarte hinzuzufügen. Die Erfahrung liegt weitgehend bei Ihnen. Sie können z. B. eine Beschreibung der Verwendung der App und einige optionale Einstellungen erhalten. Fügen Sie hier einen Anmeldeschritt ein, wenn Sie Benutzer authentifizieren müssen.

### <a name="tab-configuration-modal"></a>Tabkonfiguration modal

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Das Beispiel zeigt ein Modal der Registerkartenkonfiguration." border="false":::

### <a name="anatomy-tab-configuration-modal"></a>Anatomie: Tab-Konfiguration modal

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Abbildung, die die UI-Anatomie eines Modals der Registerkartenkonfiguration zeigt." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Logo**: Vollfarb-App-Logo Ihrer App.|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**iframe**: Responsive Space für den Inhalt Ihrer App. Zum Beispiel Tabstoppeinstellungen oder Authentifizierung.|
|4 |**Link :** Öffnet ein Dialogfeld mit weiteren Informationen zur App, z. B. eine vollständige Beschreibung, die von der App erforderlichen Berechtigungen und Links zu Ihrer Datenschutzrichtlinie und den Nutzungsbedingungen.
|5 |**Schaltfläche Schließen**: Schließt das Modal.|
|6 |**Option Teammitglieder benachrichtigen**: Das Modal fragt, ob Sie einen Beitrag erstellen möchten, der andere darüber informiert, dass Sie eine Registerkarte hinzugefügt haben.|
|7 |**Zurück-Taste**: Wechselt zum vorherigen Schritt, je nach dem Ort, an dem das Dialogfeld geöffnet wurde.|
|8 |**Schaltfläche speichern**: Schließt tab Setup ab.|

### <a name="tab-authentication-with-single-sign-on"></a>Tab-Authentifizierung mit Single Sign-On

Sie können einen Schritt hinzufügen, in dem sich Benutzer zuerst mit ihren Microsoft-Anmeldeinformationen anmelden müssen. Diese Authentifizierungsmethode wird als Single Sign-On (SSO) bezeichnet.

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Das Beispiel zeigt einen Registerkartenauthentifizierungsbildschirm." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a>Entwerfen eines Tabstopp-Setups mit UI-Vorlagen

Verwenden Sie eine der folgenden Teams UI-Vorlagen, um die Einrichtung der Registerkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind zum Sammeln, Validieren und Übermitteln von Benutzereingaben auf strukturierte Weise.
* [Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.

## <a name="view-a-tab"></a>Anzeigen einer Registerkarte

Registerkarten bieten ein umfassendes Weberlebnis in Teams in dem Sie kollaborative Inhalte – z. B. Taskboards und Dashboards – und wichtige Informationen anzeigen können.

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Das Beispiel zeigt eine Registerkarte mit einer Aufgabenplatine." border="false":::

### <a name="anatomy-tab"></a>Anatomie: Tab

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Abbildung mit der UI-Anatomie eines Tabs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Tab-Name**: Navigationsbeschriftung für Ihre Registerkarte.|
|2|**Tab-Überlauf**: Öffnet Tabstoppaktionen, z. B. Umbenennen und Entfernen.|
|3|**Tab-Chat**: Öffnet einen Chat-Thread auf der rechten Seite, so dass Benutzer eine Unterhaltung neben dem Inhalt haben.|
|4 |**iframe**: Zeigt den Inhalt Ihrer Registerkarte an.

### <a name="designing-a-tab-with-ui-templates"></a>Entwerfen einer Registerkarte mit UI-Vorlagen

Verwenden Sie eine der folgenden Teams UI-Vorlagen, um die Registerkartenzugung zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Aufgabentafel](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Aufgabenbrett, manchmal auch Kanban-Board oder Schwimmbahnen genannt, ist eine Sammlung von Karten, die oft verwendet werden, um den Status von Arbeitsaufgaben oder Tickets zu verfolgen.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Canvas mit mehreren Karten, die einen Überblick über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind zum Sammeln, Validieren und Übermitteln von Benutzereingaben auf strukturierte Weise.
* [Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.
* [Linkes Navi](../../concepts/design/design-teams-app-ui-templates.md#left-nav): Die linke Navi-Vorlage kann helfen, wenn Ihre Registerkarte eine Gewisse Navigation erfordert. Im Allgemeinen sollten Sie die Tab-Navigation auf ein Minimum beschränken.

## <a name="use-a-tab-to-collaborate"></a>Verwenden einer Registerkarte zum Zusammenarbeiten

Registerkarten erleichtern Die Unterhaltung von Inhalten an einem zentralen Ort.

### <a name="thread-discussion"></a>Threaddiskussion

Benutzer können automatisch in einen Kanal oder Chat posten, sobald sie eine neue Registerkarte hinzugefügt haben. Dadurch werden die Teammitglieder nicht nur über den neuen Inhalt informiert und ein Link zur Registerkarte zur Verfügung stellen, sondern es ermöglicht den Personen, über die Registerkarte zu sprechen.

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Das Beispiel zeigt eine Registerkarte, die in einem Kanalthread besprochen wird." border="false":::

### <a name="side-by-side-discussion"></a>Side-by-Side-Diskussion

Benutzer können als nächstes eine Unterhaltung führen, während sie den Inhalt der Registerkarte anzeigen.

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Beispiel zeigt eine Registerkarte mit einem Chat auf der rechten Seite geöffnet." border="false":::

### <a name="permissions-and-role-based-views"></a>Berechtigungen und rollenbasierte Ansichten

Die Registerkartenerfahrung kann für Benutzer je nach ihren Berechtigungen unterschiedlich sein. Beispielsweise kann ein Benutzer auf die Registerkarte zugreifen, ohne sich anmelden zu müssen. Ein anderer Benutzer muss jedoch unterschreiben und sieht etwas andere Inhalte.

## <a name="manage-a-tab"></a>Verwalten einer Registerkarte

Sie können Optionen zum Umbenennen, Entfernen oder Ändern einer Registerkarte einschließen.

### <a name="anatomy-tab-menu"></a>Anatomie: Tab-Menü

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Abbildung mit der UI-Anatomie eines Registerkartenmenüs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Einstellungen**: (Optional) Ermöglicht es Benutzern, die Einstellungen einer Registerkarte zu ändern, nachdem sie hinzugefügt wurde.|
|2|**Umbenennen**: Ermöglicht Benutzern, der Registerkarte einen Namen zu geben, der für das Team aussagekräftiger ist.|
|3|**Entfernen**: Entfernt die Registerkarte aus dem Kanal, Chat oder Besprechung.|

## <a name="tab-notifications-and-deep-linking"></a>Tab-Benachrichtigungen und Deep-Linking

Sie können eine Nachricht mit einem tiefen Link zu Ihrer Registerkarte senden. Eine Karte zeigt z. B. eine Zusammenfassung der Fehlerdaten an, die ein Benutzer auswählen kann, um den gesamten Fehler auf einer Registerkarte anzuzeigen. Das Senden von Nachrichten über Tab-Aktivität erhöht das Bewusstsein, ohne alle explizit zu benachrichtigen (d. h. Aktivitäten ohne Rauschen). Bei Bedarf können Sie auch bestimmte Benutzer @mention.

Benachrichtigen Sie Benutzer über die Registerkartenaktivität auf eine der folgenden Möglichkeiten:

* **Bot**: Diese Methode wird bevorzugt, insbesondere wenn der Tab-Thread zielgerichtet ist. Die Threadunterhaltung der Registerkarte wird als kürzlich aktiv in die Ansicht verschoben. Diese Methode ermöglicht auch eine gewisse Raffinesse bei der Art und Weise, wie die Benachrichtigung gesendet wird.
* **Meldung**: Eine Meldung wird im Aktivitätsfeed des Benutzers mit einem [tiefen Link zur Registerkarte](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true)angezeigt.

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen:

### <a name="collaboration"></a>Zusammenarbeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Die Abbildung zeigt, was mit dem Tab-Navigationsdesign zu tun ist." border="false":::

#### <a name="do-facilitate-conversation"></a>Tun: Erleichtern Sie die Unterhaltung

Schließen Sie Inhalte und Komponenten ein, über die Menschen sprechen können. Wenn es nicht in den Kontext eines Chats, Kanals oder Meetings passt, gehört es nicht zu Ihrer Registerkarte.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Das Beispiel zeigt, was nicht mit dem Tab-Navigationsdesign zu tun ist." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a>Nicht: Behandeln Sie Ihre Registerkarte wie jede andere Webseite

Eine Registerkarte ist keine Webseite, die jemand einmal anzeigen kann. Eine Registerkarte sollte Ihre wichtigsten, relevanten Inhalte anzeigen, die Menschen benötigen, um gemeinsam etwas zu erreichen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Beispiel, das zeigt, was mit dem Tab-Navigationsdesign zu tun ist." border="false":::

#### <a name="do-limit-tasks-and-data"></a>Tun: Einschränken von Aufgaben und Daten

Registerkarten funktionieren am besten, wenn sie auf bestimmte Bedürfnisse eingehen. Schließen Sie einen begrenzten Satz von Aufgaben und Daten ein, die für das Team oder die Gruppe relevant sind.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Abbildung zeigt, was nicht mit tab Navigation Design zu tun." border="false":::

#### <a name="dont-embed-your-entire-app"></a>Nicht: Einbetten Sie Ihre gesamte App

Die Verwendung einer Registerkarte zum Anzeigen einer gesamten App mit mehrstufiger Navigation und komplexen Interaktionen führt zu einer Informationsüberlastung.

   :::column-end:::
:::row-end:::

### <a name="setup"></a>Setup

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Abbildung zeigt, was mit dem Entwurf des Tab-Setups zu tun ist." border="false":::

#### <a name="do-keep-it-simple"></a>Tun: Halten Sie es einfach

Wenn Ihre App eine Authentifizierung erfordert, versuchen Sie, Microsoft Single Sign-On (SSO) zu integrieren, um eine nahtlosere Anmeldung zu ermöglichen. Enthalten auch nur wichtige Informationen und Schritte zum Hinzufügen der Registerkarte.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Abbildung zeigt, was nicht mit dem Entwurf des Tab-Setups zu tun hat." border="false":::

#### <a name="dont-have-too-many-steps"></a>Nicht: Haben Sie zu viele Schritte

Entfernen Sie alle unnötigen Schritte zum Hinzufügen einer Registerkarte.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Abbildung zeigt, was mit Tab-Theming zu tun ist." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a>Tun: Nutzen Sie Teams Farbtoken

Jedes Teams-Thema hat sein eigenes Farbschema. Um Designänderungen automatisch zu behandeln, verwenden Sie <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a> in Ihrem Entwurf.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Abbildung zeigt, was nicht mit Tab-Theming zu tun." border="false":::

#### <a name="dont-hard-code-color-values"></a>Nicht: Harte Code-Farbwerte

Wenn Sie keine Teams Farbtoken verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Anspruch.

   :::column-end:::
:::row-end:::
