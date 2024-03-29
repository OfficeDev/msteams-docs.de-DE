---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie die Entwurfsrichtlinien einschließlich UI-Elementen implementieren, um eine persönliche App mit dem Microsoft Teams UI Kit zu entwerfen.
author: heath-hamilton
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 4646d47c5aa325291f060ea192dcc1705b414ac7
ms.sourcegitcommit: bd96080c78f25eb0a67ce176df5e255be348f7b1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2022
ms.locfileid: "68575790"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Entwerfen Ihrer persönlichen App für Microsoft Teams

Eine persönliche App kann ein Bot, ein privater Arbeitsbereich oder beides sein. Manchmal dient es als Ort zum Erstellen oder Anzeigen von Inhalten. In anderen Fällen bietet es dem Benutzer eine Vogelperspektive auf alles, was seine ist, wenn die App als Registerkarte in mehreren Kanälen konfiguriert wurde.

Die folgenden Informationen beschreiben und veranschaulichen, wie Benutzer persönliche Apps in Teams hinzufügen, verwenden und verwalten können.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-Benutzeroberflächenbausatz

Im Microsoft Teams UI Kit finden Sie umfassende Richtlinien für das Design Ihrer persönlichen App, einschließlich Elementen, die Sie nach Bedarf übernehmen und ändern können. Der Benutzeroberflächenbausatz enthält auch wichtige Themen wie Barrierefreiheit und dynamische Größenanpassung, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Holen Sie sich den Microsoft Teams-Benutzeroberflächenbausatz (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Eine persönliche App hinzufügen

Benutzer können eine persönliche App aus dem Teams Store oder App-Flyout hinzufügen, indem sie das Symbol **"Mehr** " auf der linken Seite von Teams auswählen (siehe folgendes Beispiel).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Das Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen.":::

## <a name="use-a-personal-app-private-workspace"></a>Verwenden einer persönlichen App (privater Arbeitsbereich)

Mit einem privaten Arbeitsbereich können Benutzer App-Inhalte anzeigen, die für sie von Bedeutung sind, an einem zentralen Ort, ohne Teams verlassen zu müssen.

(Implementierungshinweis: Der private Arbeitsbereich basiert auf der [*persönlichen Registerkartenfunktion*](../../tabs/how-to/create-personal-tab.md).)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomie: Persönliche App (privater Arbeitsbereich)

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="Das Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Zuordnung**: Ihr App-Name.|
|B|**Registerkarten**: Ermöglicht die Navigation in Ihrer persönlichen App.|
|C|**Weiteres Menü**: Enthält weitere App-Optionen und -Informationen.|
|D|**Primäre Navigation**: Ermöglicht die Navigation zu den anderen Hauptfunktionen Ihrer App Teams.|

#### <a name="configure-and-add-multiple-actions-in-navbar"></a>**Konfigurieren und Hinzufügen mehrerer Aktionen in NavBar**

Sie können der oberen rechten Navigationsleiste mehrere Aktionen hinzufügen und ein Überlaufmenü für zusätzliche Aktionen in einer App erstellen.

>[!NOTE]
> In der Navigationsleiste können maximal fünf Aktionen hinzugefügt werden, einschließlich des Überlaufmenüs.

:::image type="content" source="../../assets/images/overflow-menu-and-multiple-actionsoptions.png" alt-text="Der Screenshot ist ein Beispiel, in dem das Menü &quot;Navigationsleiste&quot; und &quot;Überlauf&quot; beschrieben wird.":::

Rufen Sie zum **Konfigurieren und Hinzufügen mehrerer Aktionen in NavBar** die [setNavBarMenu-API](/javascript/api/@microsoft/teams-js/microsoftteams.menus?view=msteams-client-js-1.12.1&preserve-view=true) auf. und fügen Sie die `displayMode enum` Eigenschaft zu `MenuItem`hinzu. Mit `displayMode enum` dieser Eigenschaft wird definiert, wie ein Menü in der Navigationsleiste angezeigt wird. Der Standardwert von `displayMode enum` ist auf `ifRoom`.

Legen Sie basierend auf den Anforderungen und dem verfügbaren Platz in der Navigationsleiste eine der folgenden Optionen fest `displayMode enum` .

* Wenn Platz vorhanden ist, legen Sie fest `ifRoom = 0` , dass ein Element in der Navigationsleiste platziert wird.
* Wenn kein Raum vorhanden ist, legen Sie fest `overflowOnly = 1`, dass das Element immer im Überlaufmenü der Navigationsleiste, aber nicht in der Navigationsleiste platziert wird.

Es folgt ein Beispiel für die Konfiguration der Navigationsleiste mit einem Überlaufmenü für mehrere Aktionen:

```typescript
const menuItems = [item1, item2, item3, item4, item5]
microsoftTeams.menus.setNavBarMenu(menuItems, (id: string) => {
  output(`Clicked ${id}`)
  return true;
})
```

> [!NOTE]
> Die `setNavBarMenu` API steuert nicht die Schaltfläche **"Aktualisieren** ". Sie wird standardmäßig angezeigt.

:::image type="content" source="../../assets/images/overflow-menu-and-multple-actions.png" alt-text="Der Screenshot ist ein Beispiel für die Navigationsleiste und mehrere Aktionen in einem Überlaufmenü.":::

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text=" Das Beispiel zeigt die strukturelle Anatomie der persönlichen Registerkarte.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarten**: Ermöglicht die Navigation in Ihrer persönlichen App.|
|1|**webview**: Zeigt Ihre App-Inhalte an.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Dieses Beispiel zeigt die Anatomie der Komponenten der persönlichen Registerkarte.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Zuordnung**: Ihr App-Logo und -Name.|
|B|**Registerkarten**: Ermöglicht die Navigation in Ihrer persönlichen App.|
|C|**Popupansicht**: Pusht Ihre App-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.|
|D|**Weiteres Menü**: Enthält weitere App-Optionen und -Informationen. (Alternativ können Sie **"Einstellungen"** als Registerkarte festlegen.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Dieses Beispiel zeigt die strukturelle Anatomie der persönlichen Registerkarte.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarten**: Ermöglicht die Navigation in Ihrer persönlichen App.|
|1|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="design-with-ui-templates-and-advanced-components"></a>Entwerfen mit Benutzeroberflächenvorlagen und erweiterten Komponenten

Verwenden Sie eine der folgenden Teams-Vorlagen und -Komponenten, um Ihre persönliche Registerkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem übersichtlichen Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Task Board, manchmal auch als „Kanban-Board“ oder „Organisationsprozessdarstellungen“ bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Zeichenbereich mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Status](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die Vorlage „leerer Status“ kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erfahrung beim ersten Ausführen, Fehlermeldungen und vieles mehr.
* [Linker Navigationsbereich](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav): Die linke Navigationskomponente kann hilfreich sein, wenn Ihre persönliche App eine Navigation erfordert. Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.

## <a name="use-a-personal-app-bot"></a>Verwenden einer persönlichen App (Bot)

Persönliche Apps können einen Bot für 1:1-Unterhaltungen und private Benachrichtigungen enthalten (z. B. wenn ein Kollege einen Kommentar auf der Zeichenfläche postet). Benutzer interagieren mit dem Bot auf einer von Ihnen angegebenen Registerkarte.

### <a name="anatomy-personal-app-bot"></a>Anatomie: Persönliche App (Bot)

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="Das Beispiel zeigt die Anatomie der persönlichen Botkomponente.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Boteinstiegspunkt**: Einstiegspunkt für Benutzer, um auf das Botfeature in Ihrer persönlichen App zuzugreifen.|
|B|**Schaltfläche "Zurück"**: Führt Benutzer zurück in den privaten Arbeitsbereich.|
|C|**Botnachricht**: Bots senden oft Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer Adaptiven Karte).|
|D|**Kompositionsfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.|

#### <a name="configure-back-button"></a>Schaltfläche "Zurück" konfigurieren

Wenn Sie die Schaltfläche "Zurück" in einer Teams-App auswählen, kehren Sie zur Teams-Plattform zurück, ohne in der App zu navigieren.

Um innerhalb der App zu navigieren, konfigurieren Sie die Schaltfläche "Zurück", damit Sie beim Auswählen der Schaltfläche "Zurück" zu den vorherigen Schritten zurückkehren und innerhalb der App navigieren können.

Rufen **Sie zum Konfigurieren der Zurück-Schaltfläche** die [registerBackButtonHandler-API](/javascript/api/@microsoft/teams-js/pages.backstack?view=msteams-client-js-latest&preserve-view=true&branch=pr-en-us-6801&preserve-view=true) auf, die die Funktionalität der Zurück-Schaltfläche in Abhängigkeit von einer der folgenden Bedingungen behandelt:

* Wenn `registerBackButtonHandler` dieser Wert festgelegt `false`ist, ruft das JavaScript SDK die `navigateBack` API auf, und die Teams-Plattform behandelt die Schaltfläche "Zurück".
* Wenn `registerBackButtonHandler` dieser Wert festgelegt `true`ist, übernimmt die App die Funktionen der Schaltfläche "Zurück" (Sie können zu den vorherigen Schritten zurückkehren und innerhalb der App navigieren), und die Teams-Plattform führt keine weiteren Aktionen aus.

Es folgt ein Beispiel für die Konfiguration der Schaltfläche "Zurück":

```typescript
microsoftTeams.registerBackButtonHandler(() => {
  const selectOption = registerBackReturn.options[registerBackReturn.selectedIndex].value
  var isHandled = false
  if (selectOption == 'true') 
    isHandled = true;
  output(`onBack isHandled ${isHandled}`)
  return isHandled;
})
```

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text=" Das Beispiel zeigt die Anatomie der persönlichen Bot-Komponente.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Bot-Registerkarte**: Fügen Sie zum Beispiel eine **Registerkarte Chat** ein, um auf Bot-Unterhaltungen und -Benachrichtigungen zuzugreifen.|
|B|**Botnachricht**: Bots senden oft Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer Adaptiven Karte).|
|C|**Kompositionsfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.|

## <a name="manage-a-personal-tab"></a>Verwalten einer persönlichen Registerkarte

Auf der linken Seite von Teams können Benutzer mit der rechten Maustaste auf die persönliche App klicken, um sie anzuheften, zu entfernen und andere App-Optionen zu konfigurieren.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text=" Das Beispiel zeigt die Optionen für die Verwaltung einer persönlichen App.":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="tab-priority"></a>Registerkartenpriorität

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte

Bei responsiver Größe können die Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr sichtbar sein.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Das Beispiel zeigt eine persönliche App, die den relevantesten Inhalt auf der ersten Registerkarte anzeigt.":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Nicht: Lead mit sekundärem Inhalt oder Metadaten

Wie bei einer Standard-Webapplikation sollte die Navigation auf den Registerkarten in einer Reihenfolge erfolgen, die es ermöglicht, die wichtigsten Funktionen Ihrer App zu verstehen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text=" Das Beispiel zeigt eine persönliche App, die mit sekundären Inhalten oder Metadaten beginnt.":::

### <a name="tab-hierarchy"></a>Registerkartenhierarchie

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Do: Registerkarten sollten eine gleiche Hierarchie aufweisen und wichtige App-Seiten darstellen.

Ihre Registerkarten sollten die wichtigsten Funktionen und Inhalte Ihrer App kategorisieren. Bei responsiver Größe kann der Inhalt auf der rechten Seite abgeschnitten oder nicht mehr sichtbar sein.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text=" Das Beispiel zeigt eine persönliche App mit Registerkarten mit gleicher Hierarchie.":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Nicht: Unterschiedliche Hierarchieebenen einschließen

Ihr Inhalt sollte in einer logischen Reihenfolge ablaufen, die den Nutzern hilft, ihn zu verstehen. Wenn Sie zwei Registerkarten haben, die eng miteinander verbunden sind, sollten Sie sie zu einer Registerkarte zusammenfassen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text=" Das Beispiel zeigt eine persönliche App mit verschiedenen Hierarchieebenen.":::

### <a name="first-run-experience"></a>Erste Ausführung

#### <a name="do-include-a-first-run-experience"></a>Do: Einschließen einer Oberfläche für die erste Ausführung

Wenn Sie eine persönliche App zum ersten Mal verwenden, sollte zumindest ein Willkommensbildschirm erscheinen. Beschreiben Sie bei Bots, was Ihr Bot tun kann, und bieten Sie schnelle Aktionen an, wie z. B. eine Schaltfläche zum Anmelden.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text=" Das Beispiel zeigt, was Sie bei einer persönlichen App-Erstanwendung tun sollten.":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text=" Ein weiteres Beispiel zeigt, was Sie bei einer persönlichen App-Erstanwendung tun sollten.":::

#### <a name="dont-start-with-a-blank-screen"></a>Nicht: Mit einem leeren Bildschirm beginnen

Benutzer könnten verwirrt sein, wenn bei der ersten Ausführung Ihrer App nichts angezeigt wird.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text=" Das Beispiel zeigt, was Sie bei einer persönlichen App-Erstanwendung nicht tun sollten.":::

### <a name="personalized-content"></a>Personalisierte Inhalte

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Do: Aggregieren von App-Inhalten, die für einen Benutzer relevant sind

Egal, ob es sich um eine persönliche Registerkarte oder einen Bot handelt, zeigen Sie nur Inhalte an, die sich auf die Aktivitäten eines Benutzers in Ihrer App beziehen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text=" Das Beispiel zeigt, was Sie mit einer persönlichen App und personalisierten Inhalten tun können.":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text=" Ein weiteres Beispiel zeigt, was man mit einer persönlichen App und personalisierten Inhalten machen kann.":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Nicht: Nicht verknüpfte oder zu breite Inhalte anzeigen

Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, in denen der Benutzer nicht Mitglied ist. Persönliche Bot-Inhalte sollten sich auf den Einzelnen konzentrieren—nicht auf eine Gruppe.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text=" Das Beispiel zeigt, was man mit einer persönlichen App und personalisierten Inhalten nicht tun sollte.":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text=" Ein weiteres Beispiel zeigt, was man mit einer persönlichen App und personalisierten Inhalten nicht tun sollte.":::

### <a name="complex-app-features"></a>Komplexe App-Funktionen

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Do: Benutzern den Zugriff auf komplexe Features in einem Browser gestatten

Ihre App sollte sich auf die Kernaufgaben in Teams konzentrieren, aber Sie können trotzdem die vollständige, eigenständige App in einem Browser anzeigen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text=" Das Beispiel zeigt, wie Sie komplexe App-Funktionen mit einer persönlichen App verwalten können.":::

#### <a name="dont-include-your-entire-app"></a>Nicht: Ihre gesamte App einschließen

Wenn Sie Ihre App nicht speziell für Teams entwickelt haben, haben Sie wahrscheinlich Funktionen, die in einem Collaboration-Tool keinen Sinn machen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text=" Das Beispiel zeigt, wie man komplexe App-Funktionen nicht mit einer persönlichen App behandeln sollte.":::

## <a name="see-also"></a>Siehe auch

Diese anderen Designrichtlinien können je nach Umfang Ihrer persönlichen App hilfreich sein:

* [Entwerfen ihrer Registerkarte](../../tabs/design/tabs.md)
* [Entwerfen Ihres Bots](../../bots/design/bots.md)
* [registerBackButtonHandler](/javascript/api/@microsoft/teams-js/pages.backstack?view=msteams-client-js-latest&preserve-view=true&branch=pr-en-us-6801&preserve-view=true)
* [DisplayMode-Enumeration](/javascript/api/@microsoft/teams-js/menus.displaymode?view=msteams-client-js-latest&preserve-view=true)
