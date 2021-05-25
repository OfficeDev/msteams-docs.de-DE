---
title: Entwerfen Ihrer persönlichen App
description: Erfahren Sie, wie Sie Teams persönliche App entwerfen und das Microsoft Teams UI Kit erhalten.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 83fad746d71dd196f6efa6526f5c6c28ceac9e20
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644892"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a>Entwerfen Ihrer persönlichen App für Microsoft Teams

Eine persönliche App kann ein Bot, ein privater Arbeitsbereich oder beides sein. Manchmal funktioniert es wie ein Ort zum Erstellen oder Anzeigen von Inhalten, andere Mal bietet sie dem Benutzer eine Vogelperspektive über alles, was ihnen selbst ist, wenn die App als Registerkarte in mehreren Kanälen konfiguriert wurde.

Um Ihr App-Design zu leiten, wird in den folgenden Informationen beschrieben und veranschaulicht, wie Personen persönliche Apps hinzufügen, verwenden und verwalten Teams.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassende Richtlinien für das Design persönlicher Apps, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit. Das Benutzeroberflächenkit enthält auch wichtige Themen wie Barrierefreiheit und reaktionsschnelle Größenanpassung, die hier nicht behandelt werden.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a>Hinzufügen einer persönlichen App

Sie können eine persönliche App aus dem Teams Store (AppSource) oder  dem App-Flyout hinzufügen, indem Sie auf der linken Seite von Teams das Symbol Mehr auswählen (siehe das folgende Beispiel).

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Beispiel zeigt, wie Sie eine persönliche App aus dem App-Flyout hinzufügen." border="false":::

## <a name="use-a-personal-app-private-workspace"></a>Verwenden einer persönlichen App (privater Arbeitsbereich)

Mit einem privaten Arbeitsbereich können Sie App-Inhalte anzeigen, die für Sie an einem zentralen Ort von Bedeutung sind, ohne Teams.

(Implementierungshinweis: Der private Arbeitsbereich basiert auf der [*persönlichen Registerkartenfunktion.)*](../../build-your-first-app/build-personal-tab.md)

### <a name="anatomy-personal-app-private-workspace"></a>Anatomie: Persönliche App (privater Arbeitsbereich)

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Attributierung:** Ihr App-Logo und -Name.|
|B|**Registerkarten**: Bietet Navigation für Ihre persönliche App.|
|C|**Popupansicht:** Pusht Ihre App-Inhalte aus einem übergeordneten Fenster in ein eigenständiges untergeordnetes Fenster.|
|D|**Weitere Menü**: Enthält zusätzliche App-Optionen und Informationen. (Alternativ können Sie **Einstellungen** Registerkarte erstellen.)|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarten**: Bietet Navigation für Ihre persönliche App.|
|1|**iframe**: Zeigt Ihre App-Inhalte an.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="Beispiel zeigt die Komponentenanatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**App-Attribution:** Ihr App-Name.|
|B|**Registerkarten**: Bietet Navigation für Ihre persönliche App.|
|C|**Weitere Menü**: Enthält zusätzliche App-Optionen und Informationen.|
|D|**Primäre Navigation:** Stellt navigation zu Ihrer App andere Hauptfunktionen Teams zur Seite.|

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie der persönlichen Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarten**: Bietet Navigation für Ihre persönliche App.|
|1|**webview**: Zeigt Ihre App-Inhalte an.|

---

### <a name="designing-with-ui-templates-and-advanced-components"></a>Entwerfen mit Benutzeroberflächenvorlagen und erweiterten Komponenten

Verwenden Sie eine der folgenden Teams und Komponenten, um Ihre persönliche Registerkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.
* [Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.
* [Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.
* [Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.
* [Linkes](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav)Navigationsmenü: Die linke Navigationskomponente kann hilfreich sein, wenn Ihre persönliche App eine gewisse Navigation erfordert. Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.

## <a name="use-a-personal-app-bot"></a>Verwenden einer persönlichen App (Bot)

Persönliche Apps können einen Bot für Einzelunterhaltungen und private Benachrichtigungen enthalten (z. B. wenn ein Kollege einen Kommentar auf Ihrer Artboard veröffentlicht). Der Bot ist auf einer von Ihnen angegebenen Registerkarte verfügbar.

### <a name="anatomy-personal-app-bot"></a>Anatomie: Persönliche App (Bot)

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Registerkarte "Bot":** Fügen Sie beispielsweise eine Registerkarte **Chat** ein, um auf Botunterhaltungen und -benachrichtigungen zu zugreifen.|
|B|**Bot-Nachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).|
|C|**Verfassenfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="Beispiel zeigt die Anatomie der persönlichen Botkomponente." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Bot-Einstiegspunkt:** Einstiegspunkt für Benutzer, um auf das Botfeature in Ihrer persönlichen App zu zugreifen.|
|B|**Schaltfläche "Zurück":** Führt Benutzer zurück zum privaten Arbeitsbereich.|
|C|**Bot-Nachricht:** Bots senden häufig Nachrichten und Benachrichtigungen in Form einer Karte (z. B. einer adaptiven Karte).|
|D|**Verfassenfeld**: Eingabefeld zum Senden von Nachrichten an den Bot.|

---

## <a name="manage-a-personal-tab"></a>Verwalten einer persönlichen Registerkarte

Auf der linken Seite Teams Benutzer mit der rechten Maustaste auf die persönliche App klicken, um andere App-Optionen anheften, entfernen und konfigurieren.

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Beispiel zeigt Optionen zum Verwalten einer persönlichen App." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="tab-priority"></a>Registerkartenpriorität

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a>Do: Anzeigen der relevantesten Inhalte auf der ersten Registerkarte

Bei einer reaktionsschnellen Größenanpassung können Registerkarten auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Beispiel zeigt eine persönliche App, in der die relevantesten Inhalte auf der ersten Registerkarte angezeigt werden." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a>Don't: Lead with secondary content or metadata

Wie bei einer standardmäßigen Web-App sollte die Registerkartennavigation in einer Reihenfolge ausgeführt werden, die die primären Features Ihrer App sinnvoll macht.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Beispiel zeigt eine persönliche App, die mit sekundären Inhalten oder Metadaten führt." border="false":::

### <a name="tab-hierarchy"></a>Registerkartenhierarchie

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a>Do: Registerkarten sollten die gleiche Hierarchie haben und wichtige App-Seiten darstellen

Ihre Registerkarten sollten die primären Features und Inhalte Ihrer App kategorisieren. Bei einer reaktionsschnellen Größenanpassung können Inhalte auf der rechten Seite abgeschnitten oder nicht mehr angezeigt werden.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Beispiel zeigt eine persönliche App mit Registerkarten gleicher Hierarchie." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a>Don't: Include different levels of hierarchy

Ihre Inhalte sollten in einer logischen Reihenfolge ausgeführt werden, die Benutzern dabei hilft, den Inhalt sinnvoll zu nutzen. Wenn Sie über zwei Registerkarten verfügen, die eng miteinander verbunden sind, sollten Sie sie in einer Registerkarte kombinieren.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Beispiel zeigt eine persönliche App mit unterschiedlichen Hierarchieebenen." border="false":::

### <a name="first-run-experience"></a>Erste Ausführung

#### <a name="do-include-a-first-run-experience"></a>Do: Include a first-run experience

Bei der ersten Verwendung einer persönlichen App sollte mindestens ein Willkommensbildschirm angezeigt werden. Beschreiben Sie für Bots, was Ihr Bot tun kann, und stellen Sie schnelle Aktionen wie z. B. eine Anmeldeschaltfläche zur Verfügung.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Beispiel zeigt, was während einer persönlichen App beim ersten Ausführen zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Ein weiteres Beispiel zeigt, was während einer persönlichen App-Erstlauferfahrung zu tun ist." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a>Don't: Start with a blank screen

Benutzer sind möglicherweise verwirrt, wenn beim ersten Ausführen Ihrer App nichts angezeigt wird.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Beispiel zeigt, was während der ersten Ausführung einer persönlichen App nicht zu tun ist." border="false":::

### <a name="personalized-content"></a>Personalisierte Inhalte

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a>Do: Aggregieren von für einen Benutzer relevanten App-Inhalten

Unabhängig davon, ob es sich um eine persönliche Registerkarte oder einen persönlichen Bot handele, zeigen Sie Inhalte an, die sich nur auf die Aktivitäten eines Benutzers in Ihrer App bezogen haben.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Ein weiteres Beispiel zeigt, was mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a>Don't: Unrelated or overly broad content anzeigen

Zeigen Sie in persönlichen Kontexten keine Inhalte für Teams an, zu der ein Benutzer nicht gehört. Persönliche Botinhalte sollten sich auf die Person konzentrieren, nicht auf eine Gruppe.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Ein weiteres Beispiel zeigt, was nicht mit einer persönlichen App und personalisierten Inhalten zu tun ist." border="false":::

### <a name="complex-app-features"></a>Komplexe App-Features

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a>Do: Benutzern den Zugriff auf komplexe Features in einem Browser erlauben

Ihre App sollte sich auf Kernaufgaben in Teams konzentrieren, Sie können jedoch weiterhin die vollständige, eigenständige App in einem Browser anzeigen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Beispiel zeigt, wie Komplexe App-Features mit einer persönlichen App verwendet werden." border="false":::

#### <a name="dont-include-your-entire-app"></a>Don't: Include your entire app

Wenn Sie Ihre App nicht speziell für Teams erstellt haben, verfügen Sie wahrscheinlich über Features, die in einem Tool für die Zusammenarbeit keinen Sinn machen.

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Beispiel zeigt, wie komplexe App-Features nicht mit einer persönlichen App zu verarbeiten sind." border="false":::

## <a name="see-also"></a>Sehen Sie ebenfalls

Diese anderen Entwurfsrichtlinien können je nach Umfang Ihrer persönlichen App hilfreich sein:

* [Entwerfen Ihrer Registerkarte](../../tabs/design/tabs.md)
* [Entwerfen eines Bots](../../bots/design/bots.md)
